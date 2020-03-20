---
title: 'Azaltma: XML Şema Doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457743"
---
# <a name="mitigation-xml-schema-validation"></a>Azaltma: XML Şema Doğrulaması
.NET Framework 4.6'da, bileşik anahtar kullanılıyorsa ve bir anahtar boşsa XSD şema doğrulaması benzersiz kısıtlamanın ihlalini algılar.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, boş anahtarlı `xsd:unique` bileşik anahtar kullanılarak ihlal edilirse şema doğrulama hatası beklenmektedir.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bileşik bir anahtarda boş bir anahtar varsa şema doğrulama hatasının algılanıp algılanmadığı yapılandırılabilir bir özelliktir:  
  
- .NET Framework 4.6'yı hedefleyen uygulamalardan başlayarak, şema doğrulama hatasının algılanması varsayılan olarak etkinleştirilir; ancak, şema doğrulama hatası algılanmaması için bu hatayı devre dışı bırakmak mümkündür.  
  
- .NET Framework 4.6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalarda varsayılan olarak bir şema doğrulama hatası algılanmaz; ancak, şema doğrulama hatası algılanacak şekilde, bunu tercih etmek mümkündür.  
  
 Bu <xref:System.AppContext> `System.Xml.IgnoreEmptyKeySequences` davranış, anahtarın değerini tanımlamak için sınıf kullanılarak yapılandırılabilir. Anahtarın varsayılan değeri (boş anahtar dizileri göz ardı edilmez) olduğundan, `false` .NET Framework 4.6'yı hedefleyen uygulamalar anahtarın değerini ayarlamak `true`için aşağıdaki kodu kullanarak davranışı devre dışı bırakabilirsiniz:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 .NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalariçin, anahtarın `true` varsayılan değeri (boş anahtar dizileri yoksayılır) olduğundan, boş anahtara sahip bileşik anahtarın anahtarın değerini ayarlamak için aşağıdaki `false`kodu kullanarak şema doğrulama hatası oluşturduğundan emin olmak mümkündür.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
