Private-key (shared/secret-key) encryption (6) - Two parties share a key and use this key to communicate secretly.
	Message Space (M) - Defines the set of "legal messages"
	Key Space (K) - All possible keys output by Gen
	Procedures:
		Generating Key (Gen) - Probabilistic algorithm outputting a k chosen according to a distribution
		Encrypting (Enc) - Denoted as Enc_k(m), takes input key k and message m and outputs cipher text.
		Decrypting (Dec) - Denoted as Dec_k(c), takes input key k and cipher text c and outputs the message.
	Requires: For all keys output by Gen and every message in M -> Dec_k(Enc_k(m)) = m.
Shift Cipher (9 - 10) - Keyed variant of Caesar's cipher.
	M - arbitrary length strings of English letters with non letters removed
	K - {0, 1, ..., 25}
	Enc - (m_i + k) % 26
	Dec - (c_i - k) % 26
	Limited keys make it easy to decrypt
Mono-alphabetic Substitution cipher (11) - Letter maps to another letter of the alphabet one-to-one
	M - arbitrary length strings of English letters
	K - All permutations of the alphabet (26! | 2^88)
	Prone to statistical attacks since all text is static a letter mapping to e will always map to e, so finding the number of occurrences for that will logically allow an attacker to figure out what maps where.
Vigenere (poly-alphabetic shift) cipher (13) - An arbitrary number of letters (>=2) maps to the same arbitrary number of letters. (ab -> DZ, ac -> TY). 
	![[Pasted image 20240902113213.png]]
	Period (t) - Length of key
	The Attack (14) - Knowing t makes deciphering this cipher easier. The key can then be written as k = k_1 ... k_t for character k_i in k. c can be divided into t parts each being encrypted with a cipher j in {1, ..., t} (c_j, c_j+t, c_j+2t ...) which are just shifted by k_j. Then for each t stream the matching k value needs to be found to deduce the right probability distribution. The total computation for this attack is 26 * t
	Secure as long as the key is as long as what is being encrypted
Threat models (19-20)
	Ciphertext-only attack - Only cipher text is observed and information about plaintext is drawn purely from that.
	Known-plaintext attack - One or more plaintext/ciphertext pairs is known, the attacker then uses that key to try to deduce other plaintext from given ciphertexts.
	Chosen-plaintext attack - Same as above, but the attacker has the ability to choose plaintexts of its choice.
	Chose-ciphertext attack - Attacker obtains information about the decryption of ciphertexts of its choice.
