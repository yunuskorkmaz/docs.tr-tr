---
title: 'Azaltma: XML Şema Doğrulaması'
description: Bir bileşik anahtar kullanılmışsa ve .NET Framework 4,6 ' de bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 0672361ca5c0bc7cb6ec166f59278b93555e0947
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475313"
---
# <a name="mitigation-xml-schema-validation"></a>Azaltma: XML Şema Doğrulaması
.NET Framework 4,6 ' de, bir bileşik anahtar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, `xsd:unique` boş bir anahtarla bir bileşik anahtar kullanılarak ihlal edilirse bir şema doğrulama hatası beklenmektedir.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bir bileşik anahtarda bir boş anahtar varsa bir şema doğrulama hatası algılanıp algılanmayacağı, yapılandırılabilir bir özelliktir:  
  
- .NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, şema doğrulama hatası algılama işlemi varsayılan olarak etkindir; Ancak, şema doğrulama hatası algılanmayacak şekilde devre dışı bırakmak mümkündür.  
  
- .NET Framework 4,6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatasının algılanabilmesi için onu kabul etmek mümkündür.  
  
 Bu davranış, <xref:System.AppContext> anahtarın değerini tanımlamak için sınıfı kullanılarak yapılandırılabilir `System.Xml.IgnoreEmptyKeySequences` . Anahtarın varsayılan değeri `false` (boş anahtar dizileri yoksayılamadığından) olduğundan, .NET Framework 4,6 ' i hedefleyen uygulamalar, anahtarın değerini olarak ayarlamak için aşağıdaki kodu kullanarak davranışı geri alabilir `true` :  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalar için, anahtarın varsayılan değeri `true` (boş anahtar dizileri yoksayıldı) olduğundan, boş anahtara sahip bir bileşik anahtarın, anahtarın değerini olarak ayarlamak için aşağıdaki kodu kullanarak bir şema doğrulama hatası oluşturduğundan emin olabilirsiniz `false` .  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
