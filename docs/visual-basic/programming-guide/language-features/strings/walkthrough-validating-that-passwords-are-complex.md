---
title: Parola karmaşıklığı doğrulanıyor
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 6e8697379a6fbb5cc15b60291e5b822897c2c013
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348323"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>İzlenecek yol: Parolaların Karmaşık Olduğunu Doğrulama (Visual Basic)
Bu yöntem, bazı güçlü parola özelliklerini denetler ve parolanın başarısız olup olmadığını kontrol eden bilgilerle bir dize parametresini güncelleştirir.  
  
 Parolalar, bir kullanıcıyı yetkilendirmek için güvenli bir sistemde kullanılabilir. Ancak, yetkisiz kullanıcıların tahmin edilmesi için parolaların kullanılması zor olmalıdır. Saldırganlar bir Sözlükteki tüm sözcükleri (veya farklı dillerdeki birden çok sözlükleri) kullanarak bir *sözlük saldırı* programı kullanabilir ve sözcüklerin birinin Kullanıcı parolası olarak çalışıp çalışmadığını sınar. "Yankees" veya "Mustang" gibi zayıf parolalar hızlı bir şekilde tahmin edilebilir. Daha güçlü parolalar (örneğin, "? 'L1N3vaFiNdMeyeP@sSWerd! ", tahmin edilebilir olma olasılığını çok daha az. Parola korumalı bir sistem, kullanıcıların güçlü parolalar seçmesini sağlamalıdır.  
  
 Güçlü bir parola karmaşıktır (büyük harf, küçük harf, sayısal ve özel karakterlerin bir karışımını içeren) ve bir sözcük değildir. Bu örnek, karmaşıklığın nasıl doğrulanacağını göstermektedir.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu parolayı içeren dizeyi geçirerek bu yöntemi çağırın.  
  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Text.RegularExpressions> ad alanının üyelerine erişin. Kodunuzda üye adlarını tam olarak nitedıysanız `Imports` bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Güvenlik  
 Parolayı bir ağ üzerinden taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmanız gerekir. Daha fazla bilgi için bkz. [ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Daha fazla karmaşıklık denetimi ekleyerek `ValidatePassword` işlevinin doğruluğunu geliştirebilirsiniz:  
  
- Parolayı ve alt dizelerini kullanıcının adı, Kullanıcı tanımlayıcısı ve uygulama tanımlı bir sözlükten karşılaştırın. Ayrıca, karşılaştırmaları gerçekleştirirken görsel açıdan benzer karakterleri eşdeğer olarak değerlendirin. Örneğin, "l" ve "e" harflerini "1" ve "3" sayılarıyla eşdeğer olarak değerlendirin.  
  
- Yalnızca bir büyük harf karakteri varsa, parolanın ilk karakteri olmadığından emin olun.  
  
- Parolanın son iki karakterinin harf karakter olduğundan emin olun.  
  
- Klavyenin en üst satırından tüm simgelerin girildiği parolalara izin vermeyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
