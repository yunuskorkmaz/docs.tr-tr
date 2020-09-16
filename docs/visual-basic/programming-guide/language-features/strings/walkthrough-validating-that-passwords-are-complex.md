---
title: Parola karmaşıklığı doğrulanıyor
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 8cb04286e98cf78f0fb66dde92002ee09e2ea0f5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556251"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>İzlenecek yol: Parolaların Karmaşık Olduğunu Doğrulama (Visual Basic)
Bu yöntem, bazı güçlü parola özelliklerini denetler ve parolanın başarısız olup olmadığını kontrol eden bilgilerle bir dize parametresini güncelleştirir.  
  
 Parolalar, bir kullanıcıyı yetkilendirmek için güvenli bir sistemde kullanılabilir. Ancak, yetkisiz kullanıcıların tahmin edilmesi için parolaların kullanılması zor olmalıdır. Saldırganlar bir Sözlükteki tüm sözcükleri (veya farklı dillerdeki birden çok sözlükleri) kullanarak bir *sözlük saldırı* programı kullanabilir ve sözcüklerin birinin Kullanıcı parolası olarak çalışıp çalışmadığını sınar. "Yankees" veya "Mustang" gibi zayıf parolalar hızlı bir şekilde tahmin edilebilir. Daha güçlü parolalar (örneğin, "? ' L1N3vaFiNdMeyeP@sSWerd ! ", Tahmin edilebilir olma olasılığı çok daha az. Parola korumalı bir sistem, kullanıcıların güçlü parolalar seçmesini sağlamalıdır.  
  
 Güçlü bir parola karmaşıktır (büyük harf, küçük harf, sayısal ve özel karakterlerin bir karışımını içeren) ve bir sözcük değildir. Bu örnek, karmaşıklığın nasıl doğrulanacağını göstermektedir.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Kodu derle  
 Bu parolayı içeren dizeyi geçirerek bu yöntemi çağırın.  
  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Text.RegularExpressions>Ad alanının üyelerine erişin. `Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Güvenlik  
 Parolayı bir ağ üzerinden taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmanız gerekir. Daha fazla bilgi için bkz. [ASP.NET Web uygulaması güvenliği](/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 `ValidatePassword`Ek karmaşıklık denetimleri ekleyerek işlevin doğruluğunu artırabilirsiniz:  
  
- Parolayı ve alt dizelerini kullanıcının adı, Kullanıcı tanımlayıcısı ve uygulama tanımlı bir sözlükten karşılaştırın. Ayrıca, karşılaştırmaları gerçekleştirirken görsel açıdan benzer karakterleri eşdeğer olarak değerlendirin. Örneğin, "l" ve "e" harflerini "1" ve "3" sayılarıyla eşdeğer olarak değerlendirin.  
  
- Yalnızca bir büyük harf karakteri varsa, parolanın ilk karakteri olmadığından emin olun.  
  
- Parolanın son iki karakterinin harf karakter olduğundan emin olun.  
  
- Klavyenin en üst satırından tüm simgelerin girildiği parolalara izin vermeyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web uygulaması güvenliği](/previous-versions/aspnet/330a99hc(v=vs.100))
