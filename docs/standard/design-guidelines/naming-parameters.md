---
title: Adlandırma parametreleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6a8a1dcdcb8fa3311b040c72987f0f76e681fc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086478"
---
# <a name="naming-parameters"></a>Adlandırma parametreleri
Okunabilirlik belirgin nedenini görsel tasarım araçlarını, IntelliSense ve gözatma işlevselliği sınıf sağladığınızda parametreleri belgelerinde ve Tasarımcısı'nda görüntülenen olduğundan, parametre isimleri için yönergeleri izlemeniz önemlidir.  
  
 **✓ DO** camelCasing parametre adları kullanın.  
  
 **✓ DO** açıklayıcı parametre adları kullanın.  
  
 **✓ CONSIDER** parametrenin türü yerine bir parametrenin anlamı dayalı adları kullanarak.  
  
### <a name="naming-operator-overload-parameters"></a>Adlandırma işleci aşırı yükleme parametreleri  
 **✓ DO** kullanmak `left` ve `right` parametreleri için hiçbir anlamı ise ikili İşleç aşırı yüklemesi parametre adları için.  
  
 **✓ DO** kullanmak `value` için birli işleç aşırı yüklemesi parametre adları parametreleri için hiçbir anlamı ise.  
  
 **✓ CONSIDER** anlamlı adlar işleci aşırı yükleme parametreleri bunun nedenle önemli değer eklerse.  
  
 **X DO NOT** kullanım kısaltmalar veya sayısal dizinlerini işleci için aşırı yükleme parametre adları.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
