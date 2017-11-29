---
title: "Eşitlik İşleçleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55c0505f5a06dfc87897fa59e9d6083cbd63c8ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="equality-operators"></a>Eşitlik İşleçleri
Bu bölümde tekrar yüklemesi eşitlik işleçleri açıklanır ve başvurduğu `operator==` ve `operator!=` eşitlik işleçleri olarak.  
  
 **X yok** eşitlik işleçleri ve diğer aşırı yükleme.  
  
 **✓ YAPMAK** emin <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiği ve benzer performans özellikleri vardır.  
  
 Bu genellikle anlamına `Object.Equals` eşitlik işleçleri aşırı zaman geçersiz kılınacak gerekiyor.  
  
 **KAÇININ x** eşitlik işleçleri özel durumları atma.  
  
 Örneğin, bağımsız değişkenlerden biri atma yerine null ise false döndürür `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Değer türleri üzerinde eşitlik işleçleri  
 **✓ YAPMAK** eşitlik anlamlı ise, değer türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Çoğu programlama dillerinde hiçbir varsayılan uygulaması olduğundan `operator==` değer türleri için.  
  
## <a name="equality-operators-on-reference-types"></a>Başvuru türleri üzerinde eşitlik işleçleri  
 **KAÇININ x** kesilebilir başvuru türleri üzerinde eşitlik işleçleri aşırı yükleme.  
  
 Birçok dilin başvuru türleri için yerleşik eşitlik işleçleri vardır. Yerleşik genellikle başvuru eşitliği işleçler ve varsayılan davranışı için değer eşitliği değiştirildiğinde, geliştiricilerin çoğu Şaşkın.  
  
 Girişi çok referans eşitlik ve değer eşitliği arasındaki fark zorlaştıran çünkü bu sorunu değişmez başvuru türlerinde azalır.  
  
 **KAÇININ x** uygulama önemli ölçüde daha yavaş, başvuru eşitliği olacaksa başvuru türlerinde eşitlik işleçleri aşırı yükleme.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
