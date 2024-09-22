





int nbrEights(int amount, int giftees) {
		for (int k = giftees; k >= 0; k--) {
			int amount_remaining = amount - 8 * k;
			int giftees_remaining = giftees - k;

			// Each remaining giftee must receive at least 1
			if (amount_remaining < giftees_remaining) continue;

			// Cannot assign amounts if no giftees remain but amount is left
			if (giftees_remaining == 0) {
				if (amount_remaining == 0) return k;
				else continue;
			}

			// Check for the impossible case
			if (amount_remaining == 4 && giftees_remaining == 1) continue;

			// Valid distribution found
			return k;
		}
		return 0; // If no valid distribution is found
	}