---
title: "Doğrulama Parolalar karmaşıklık (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>İzlenecek yol: Parolaların Karmaşık Olduğunu Doğrulama (Visual Basic)
Bu yöntem, bazı güçlü parola özelliklerini denetler ve bir dize parametresi hakkında Parola denetimlerini başarısız bilgilerle güncelleştirir.  
  
 Parolaları güvenli bir sistemde bir kullanıcı yetki vermek için kullanılabilir. Ancak, parolalar yetkisiz kullanıcıların tahmin zor olması gerekir. Saldırganlar kullanabileceğiniz bir *sözlük saldırısı* tüm bir sözlük (veya birden çok sözlükler farklı dillerde) sözcükleri dolaşır ve herhangi bir sözcük bir kullanıcının parolasını çalışıp çalışmadığını test program. "Yankees'i" veya "Mustang" gibi Zayıf parolalar kolayca tahmin edilebilir. Daha güçlü parolalar gibi "? 'L1N3vaFiNdMeyeP@sSWerd! ", Tahmin edilebilir daha az olasıdır. Parola korumalı bir sistem kullanıcıların güçlü parolalar seçtiğinizden emin olun.  
  
 Güçlü bir parola (büyük harf, küçük harfler, sayısal ve özel karakterler bir karışımını içeren) karmaşıktır ve bir sözcük değil. Bu örnek, karmaşıklık doğrulamak gösterilmiştir.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu parolayı içeren dize geçirerek bu yöntemi çağırın.  
  
 Bu örnek gerektirir:  
  
-   Üye erişimi <xref:System.Text.RegularExpressions> ad alanı. Ekleme bir `Imports` üye adlarının kodunuzda tam olarak niteleyemiyorsanız deyimi. Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Güvenlik  
 Bir ağ üzerinden parola taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmak gerekir. Daha fazla bilgi için bkz: [ASP.NET Web uygulaması güvenliği](https://msdn.microsoft.com/library/330a99hc).  
  
 Doğruluğunu artırabilir `ValidatePassword` karmaşıklık denetimler ekleyerek işlevi:  
  
-   Parola ve onun alt dizeler kullanıcının adını, kullanıcı kimliği ve bir uygulama tanımlı sözlük karşı karşılaştırın. Ayrıca, görsel olarak benzer karakterler karşılaştırmaları gerçekleştirilirken eşdeğer olarak kabul eder. Örneğin, harf "m" ve "e" eşdeğer rakamları "1" ve "3" olarak kabul eder.  
  
-   Yalnızca bir büyük harf karakter ise, parolanın ilk karakter olmadığından emin olun.  
  
-   Parolanın Son iki karakterler harf karakterler olduğundan emin olun.  
  
-   Klavyenin ilk satırdaki tüm sembolleri girilen parolalar izin vermez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.RegularExpressions.Regex>  
 [ASP.NET Web uygulaması güvenliği](https://msdn.microsoft.com/library/330a99hc)
