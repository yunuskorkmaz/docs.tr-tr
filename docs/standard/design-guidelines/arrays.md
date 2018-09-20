---
title: Diziler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ac7e28c3172f2ed68d402e1d04a1664644c7f25
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324717"
---
# <a name="arrays"></a>Diziler
**✓ DO** ortak API'ler dizilerde üzerinden koleksiyonları kullanmayı tercih. [Koleksiyonları](../../../docs/standard/design-guidelines/guidelines-for-collections.md) bölüm koleksiyonları ve dizileri arasında seçim yapma hakkında ayrıntılı bilgi sağlar.  
  
 **X DO NOT** salt okunur dizi alanları kullanın. Alanı salt okunur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.  
  
 **✓ CONSIDER** basit dizileri çok boyutlu diziler yerine kullanma.  
  
 Basit bir dizi, diziler de olan öğeler ile bir dizidir. Öğeleri dizileri çok boyutlu diziler için kıyasla daha az harcanmış bazı (örn. seyrek matris) veri kümeleri için önde gelen farklı boyutlarda olabilir. Ayrıca, bazı senaryolarda daha iyi çalışma zamanı performansı göstermesi şekilde CLR basit diziler, dizin işlemleri iyileştirir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
