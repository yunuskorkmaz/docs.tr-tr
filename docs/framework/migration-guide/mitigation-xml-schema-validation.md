---
title: 'Azaltma: XML Şema Doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457743"
---
# <a name="mitigation-xml-schema-validation"></a>Azaltma: XML Şema Doğrulaması
.NET Framework 4,6 ' de, bir bileşik anahtar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, `xsd:unique` boş bir anahtarla bileşik anahtar kullanılarak ihlal edilirse bir şema doğrulama hatası beklenmektedir.  
  
## <a name="mitigation"></a>Azaltma  
 Bir bileşik anahtarda bir boş anahtar varsa bir şema doğrulama hatası algılanıp algılanmayacağı, yapılandırılabilir bir özelliktir:  
  
- .NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, şema doğrulama hatası algılama işlemi varsayılan olarak etkindir; Ancak, şema doğrulama hatası algılanmayacak şekilde devre dışı bırakmak mümkündür.  
  
- .NET Framework 4,6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatasının algılanabilmesi için onu kabul etmek mümkündür.  
  
 Bu davranış, `System.Xml.IgnoreEmptyKeySequences` anahtarın değerini tanımlamak için <xref:System.AppContext> sınıfı kullanılarak yapılandırılabilir. Anahtarın varsayılan değeri `false` (boş anahtar dizileri yok sayılıyor), .NET Framework 4,6 ' i hedefleyen uygulamalar, anahtarın değerini `true`olarak ayarlamak için aşağıdaki kodu kullanarak davranışı geri alabilir:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalar için, anahtarın varsayılan değeri `true` (boş anahtar dizileri yoksayıldı), boş anahtara sahip bir bileşik anahtarın, bir şema doğrulama hatası oluşturduğundan Aşağıdaki kod, anahtarın değerini `false`olarak ayarlamak için.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
