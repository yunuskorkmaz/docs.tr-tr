---
title: Eşitlik İşleçleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 31a5ce18f4526b5e3b8411365dff812601de87ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709445"
---
# <a name="equality-operators"></a>Eşitlik İşleçleri
Bu bölümde eşitlik işleçlerini aşırı yükleme ve `operator==` ve eşitlik işleçleri olarak `operator!=` açıklanır.  
  
 **X DO NOT** eşitlik işleçleri ve diğer aşırı yükleme.  
  
 **✓ DO** emin <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiği ve benzer performans özellikleri vardır.  
  
 Bu genellikle eşitlik işleçleri aşırı yüklendiğinde `Object.Equals` geçersiz kılınmasının gerektiği anlamına gelir.  
  
 **X AVOID** eşitlik işleçleri özel durumları atma.  
  
 Örneğin, `NullReferenceException`yapmak yerine bağımsız değişkenlerden biri null ise false döndürün.  
  
## <a name="equality-operators-on-value-types"></a>Değer türlerinde eşitlik Işleçleri  
 **✓ DO** eşitlik anlamlı ise, değer türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Çoğu programlama dilinde, değer türleri için `operator==` varsayılan bir uygulama yoktur.  
  
## <a name="equality-operators-on-reference-types"></a>Başvuru türlerinde eşitlik Işleçleri  
 **X AVOID** kesilebilir başvuru türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Birçok dilde başvuru türleri için yerleşik eşitlik işleçleri vardır. Yerleşik operatörler genellikle başvuru eşitliğini uygular ve varsayılan davranış değer eşitliğine değiştirildiğinde çok sayıda geliştirici şaşırtır.  
  
 Bu sorun, sabit başvuru türleri için azaltıldığı için, değişiklik, başvuru eşitliği ve değer eşitlik arasındaki farkı fark ettiğini çok daha zor hale getirir.  
  
 **X AVOID** uygulama önemli ölçüde daha yavaş, başvuru eşitliği olacaksa başvuru türlerinde eşitlik işleçleri aşırı yükleme.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
