---
title: 'Azaltma: XML şema doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f9475a978ddf7253833e6c3372049d24502f95
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300578"
---
# <a name="mitigation-xml-schema-validation"></a>Azaltma: XML şema doğrulaması
.NET Framework 4.6, XSD şema doğrulaması benzersiz kısıtlama ihlalini bir bileşik anahtarı kullanılır ve bir anahtar boş ise algılar.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin etkisini en az olmalıdır: şema belirtimine göre bir şema doğrulama hatası varsa beklenmektedir `xsd:unique` boş bir anahtara sahip bir bileşik anahtarı kullanarak ihlal etti.  
  
## <a name="mitigation"></a>Azaltma  
 Boş bir anahtarı bir bileşik anahtarı varsa, şema doğrulama hatası olup olmadığını tespit yapılandırılabilir bir özelliktir:  
  
- Şema doğrulama hatası olan algılama, .NET Framework 4.6 hedefleyen uygulamaları ile başlayarak, varsayılan olarak etkindir; böylece şema doğrulama hatası algılanmadı ancak bunun dışında bırakmak mümkündür.  
  
- .NET Framework 4. 6'altında çalışır ancak .NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatası algılandı böylece buna, iyileştirilmiş mümkündür.  
  
 Bu davranış kullanarak yapılandırılabilir <xref:System.AppContext> değerini tanımlamak için sınıf `System.Xml.IgnoreEmptyKeySequences` geçin. Anahtarın varsayılan değeri olduğundan `false` (boş anahtar dizileri yok sayılır), .NET Framework 4.6 hedefleyen uygulamalar iyileştirilmiş davranışı iptal anahtarın değeri ayarlamak için aşağıdaki kodu kullanarak `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Anahtarın varsayılan değeri olduğundan .NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalar için `true` (boş anahtar dizileri yok sayılır), boş bir anahtara sahip bir bileşik anahtarı kullanarak bir şema doğrulama hatası üretin emin olmak mümkündür anahtarın değeri ayarlamak için aşağıdaki kodu `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
