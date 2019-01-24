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
author: KrzysztofCwalina
ms.openlocfilehash: ef1a0aff1ac59434d9d9a6f0371bf236f637050e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572688"
---
# <a name="equality-operators"></a>Eşitlik İşleçleri
Bu bölümde, aşırı yüklerken eşitlik işleci açıklar ve başvurduğu `operator==` ve `operator!=` eşitlik işleçleri olarak.  
  
 **X DO NOT** eşitlik işleçleri ve diğer aşırı yükleme.  
  
 **✓ DO** emin <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiği ve benzer performans özellikleri vardır.  
  
 Bu genellikle anlamına `Object.Equals` eşitlik operatörleri aşırı yüklendiğinde geçersiz kılınması gerekiyor.  
  
 **X AVOID** eşitlik işleçleri özel durumları atma.  
  
 Örneğin, bağımsız değişkenlerden biri oluşturmak yerine null ise yanlış geri `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Değer türleri üzerinde eşitlik işleçleri  
 **✓ DO** eşitlik anlamlı ise, değer türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Çoğu programlama dilinde, hiçbir varsayılan uygulaması olduğundan `operator==` değer türleri için.  
  
## <a name="equality-operators-on-reference-types"></a>Başvuru türlerinde eşitlik işleçleri  
 **X AVOID** kesilebilir başvuru türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Birçok dil başvuru türleri için yerleşik eşitlik işleçleri sahip. Yerleşik işleçler, genellikle başvuru eşitliği uygulamak ve birçok geliştiricinin varsayılan davranışı için değer eşitliği değiştirildiğinde şaşırmayın.  
  
 Bu sorun, değiştirilemezlik çok başvuru eşitliği değer eşitliği arasındaki fark zorlaştırır çünkü değişmez başvuru türleri için azalır.  
  
 **X AVOID** uygulama önemli ölçüde daha yavaş, başvuru eşitliği olacaksa başvuru türlerinde eşitlik işleçleri aşırı yükleme.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
