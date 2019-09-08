---
title: Mayı XML şema doğrulaması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f53a2e8684029c0d1329d29a88bd1788e62d43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789671"
---
# <a name="mitigation-xml-schema-validation"></a>Mayı XML şema doğrulaması
.NET Framework 4,6 ' de, bir bileşik anahtar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, boş bir anahtarla bir bileşik anahtar kullanılarak ihlal edilirse bir şema `xsd:unique` doğrulama hatası beklenmektedir.  
  
## <a name="mitigation"></a>Azaltma  
 Bir bileşik anahtarda bir boş anahtar varsa bir şema doğrulama hatası algılanıp algılanmayacağı, yapılandırılabilir bir özelliktir:  
  
- .NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, şema doğrulama hatası algılama işlemi varsayılan olarak etkindir; Ancak, şema doğrulama hatası algılanmayacak şekilde devre dışı bırakmak mümkündür.  
  
- .NET Framework 4,6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatasının algılanabilmesi için onu kabul etmek mümkündür.  
  
 Bu davranış, <xref:System.AppContext> `System.Xml.IgnoreEmptyKeySequences` anahtarın değerini tanımlamak için sınıfı kullanılarak yapılandırılabilir. Anahtarın varsayılan değeri `false` (boş anahtar dizileri yoksayılamadığından) olduğundan, .NET Framework 4,6 ' i hedefleyen uygulamalar, anahtarın değerini olarak `true`ayarlamak için aşağıdaki kodu kullanarak davranışı geri alabilir:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalar için, anahtarın varsayılan değeri (boş anahtar dizileri yoksayıldı) `true` olduğundan, boş anahtara sahip bir bileşik anahtarın, kullanarak bir şema doğrulama hatası ürettiğinden emin olmak mümkündür. anahtarın değerini olarak `false`ayarlamak için aşağıdaki kod.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6.md)
