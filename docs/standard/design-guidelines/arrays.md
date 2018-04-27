---
title: Diziler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54f5d68a343f473c67484e9e806551eb115bac36
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="arrays"></a>Diziler
**✓ YAPMAK** ortak API'ler dizilerde üzerinden koleksiyonları kullanmayı tercih. [Koleksiyonları](../../../docs/standard/design-guidelines/guidelines-for-collections.md) bölüm koleksiyonları ve diziler arasında seçim yapma hakkında ayrıntılı bilgi sağlar.  
  
 **X yok** salt okunur dizi alanları kullanın. Alan salt okunurdur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.  
  
 **✓ DÜŞÜNÜN** basit dizileri çok boyutlu diziler yerine kullanma.  
  
 Basit dizi de diziler öğeleri ile bir dizidir. Öğeleri olun dizileri çok boyutlu diziler kıyasla daha az harcanan alan bazı (örn., seyrek matris) veri kümeleri için önde gelen farklı boyutlarda olabilir. Ayrıca, bazı senaryolarda daha iyi çalışma zamanı performans sergiler şekilde CLR basit diziler üzerinde dizin işlemleri iyileştirir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
