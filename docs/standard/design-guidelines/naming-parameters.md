---
title: Adlandırma Parametreleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709185"
---
# <a name="naming-parameters"></a>Adlandırma Parametreleri
Görsel tasarım araçları IntelliSense ve sınıf tarama işlevselliği sağladığınızda, bir okunabilirlik işleminin belirgin olmasının ötesinde parametre adları için yönergeleri izlemek önemlidir.  
  
 **✓ DO** camelCasing parametre adları kullanın.  
  
 **✓ DO** açıklayıcı parametre adları kullanın.  
  
 **✓ CONSIDER** parametrenin türü yerine bir parametrenin anlamı dayalı adları kullanarak.  
  
### <a name="naming-operator-overload-parameters"></a>Adlandırma Işleci aşırı yükleme parametreleri  
 **✓ DO** kullanmak `left` ve `right` parametreleri için hiçbir anlamı ise ikili İşleç aşırı yüklemesi parametre adları için.  
  
 **✓ DO** kullanmak `value` için birli işleç aşırı yüklemesi parametre adları parametreleri için hiçbir anlamı ise.  
  
 **✓ CONSIDER** anlamlı adlar işleci aşırı yükleme parametreleri bunun nedenle önemli değer eklerse.  
  
 **X DO NOT** kullanım kısaltmalar veya sayısal dizinlerini işleci için aşırı yükleme parametre adları.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
