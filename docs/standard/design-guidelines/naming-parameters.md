---
title: Adlandırma parametreleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 35965f03f5c50cbe3ffcc9bdb615d99c50fc30a2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147924"
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
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
