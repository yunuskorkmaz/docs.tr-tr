---
title: 'Azaltma: XML şema doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5c0087412a53177a7c43df838266f6d896c1bd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220480"
---
# <a name="mitigation-xml-schema-validation"></a>Azaltma: XML şema doğrulaması
İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD şema doğrulaması bir bileşik anahtarı kullanılır ve bir anahtar ise boş bir Benzersizlik kısıtlamasını ihlal algılar.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin etkisini en az olmalıdır: şema belirtimine göre bir şema doğrulama hatası varsa beklenmektedir `xsd:unique` boş bir anahtara sahip bir bileşik anahtarı kullanarak ihlal etti.  
  
## <a name="mitigation"></a>Azaltma  
 Boş bir anahtarı bir bileşik anahtarı varsa, şema doğrulama hatası olup olmadığını tespit yapılandırılabilir bir özelliktir:  
  
-   Hedefleyen uygulamaları ile başlayan [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], şema doğrulama hatası olan algılama, varsayılan olarak etkindir; böylece şema doğrulama hatası algılanmadı ancak bunun dışında bırakmak mümkündür.  
  
-   Altında çalışan uygulamalar, [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ancak hedef [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] ve önceki sürümlerinde, varsayılan olarak bir şema doğrulama hatası algılanmadı; böylece şema doğrulama hatası algılandı ancak, bunu geri çevirmek mümkündür.  
  
 Bu davranış kullanarak yapılandırılabilir <xref:System.AppContext> değerini tanımlamak için sınıf `System.Xml.IgnoreEmptyKeySequences` geçin. Anahtarın varsayılan değeri olduğundan `false` (boş anahtar dizileri yok sayılır), hedefleyen uygulamaları [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] davranışı iptal anahtarın değeri ayarlamak için aşağıdaki kodu kullanarak iyileştirilmiş `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Hedefleyen uygulamalar için [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] ve önceki sürümleri, anahtarın varsayılan değeri olduğundan `true` (boş anahtar dizileri yok sayılır), boş bir anahtara sahip bir bileşik anahtarı kullanarak bir şema doğrulama hatası üretin emin olmak mümkündür Aşağıdaki kod, anahtarın değeri ayarlamak için `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
