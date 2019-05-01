---
title: Parolalar karmaşıklık (Visual Basic) doğrulanıyor
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938261"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>İzlenecek yol: Parolaların karmaşık olduğunu doğrulama (Visual Basic)
Bu yöntem, bazı güçlü parola özelliklerini denetler ve bir dize parametresi başarısız parola denetleyen hakkında bilgilerle güncelleştirir.  
  
 Parolalar güvenli bir sistemde bir kullanıcıyı yetkilendirmek için kullanılabilir. Ancak, parola yetkisiz kullanıcıların tahmin zor olması gerekir. Saldırganlar kullanabileceğiniz bir *sözlük saldırıları* tüm bir sözlük (veya birden çok sözlükleri farklı dillerde) bir kelimelerin gezinir ve herhangi bir kelimelerin bir kullanıcının parolasını çalışıp çalışmadığını test programı. Zayıf parolalarda "Yankees'in" veya "Mustang" gibi hızlı bir şekilde tahmin edilebilir. Güçlü parolalar gibi "? 'L1N3vaFiNdMeyeP@sSWerd! ", Tahmin edilebilir çok daha düşüktür. Parola korumalı bir sistem kullanıcıların güçlü parolalar seçtiğinizden emin olun.  
  
 Güçlü bir parola (büyük harf, küçük harfler, sayısal ve özel karakterler bir karışımını içeren) karmaşıktır ve bir sözcük değildir. Bu örnek, karmaşıklık doğrulamak nasıl gösterir.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu parolayı içeren dizeyi geçirerek bu yöntemi çağırın.  
  
 Bu örnek gerektirir:  
  
- Üye erişimi <xref:System.Text.RegularExpressions> ad alanı. Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Güvenlik  
 Parola ağ üzerinden taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmanız gerekir. Daha fazla bilgi için [ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Doğruluğunu geliştirebilir `ValidatePassword` karmaşıklık denetimleri ekleyerek işlevi:  
  
- Parola ve onun alt dizeler kullanıcının adını, kullanıcı kimliği ve uygulama tanımlı bir sözlük karşı karşılaştırın. Ayrıca, görsel olarak benzer karakterler karşılaştırmaları yaparken eşdeğer olarak kabul eder. Örneğin, "e" ve "m" harf "1" ve "3" simgeleridir eşdeğer olarak kabul eder.  
  
- Yalnızca bir büyük harf karakter varsa, parolanın ilk karakteri olmadığından emin olun.  
  
- Parola en son iki karakter harf karakterler olduğundan emin olun.  
  
- Klavyenin üst satırdaki tüm sembolleri girilen parolaları izin vermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
