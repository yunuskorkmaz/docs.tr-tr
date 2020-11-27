---
title: Derleme Yerleştirme
description: Dizinler içindeki .NET derleme yerleştirmesi için yönergeleri gözden geçirin (örneğin, genel derleme önbelleğinde veya uygulamanın dizininde veya alt dizininde).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 15ff6edf5887062b0cce918b39beef6c9b618ca2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271558"
---
# <a name="assembly-placement"></a>Derleme Yerleştirme

Çoğu .NET Framework uygulaması için, uygulamayı oluşturan derlemeleri uygulama dizininde, uygulama dizininin bir alt dizininde veya genel derleme önbelleğinde (derleme paylaşılıyorsa) bulursunuz. Bir yapılandırma dosyasındaki [ \<codeBase> öğesini](../configure-apps/file-schema/runtime/codebase-element.md) kullanarak ortak dil çalışma zamanının bir derlemeyi aradığı yeri geçersiz kılabilirsiniz. Derlemenin tanımlayıcı bir adı yoksa, [ \<codeBase> öğesi](../configure-apps/file-schema/runtime/codebase-element.md) kullanılarak belirtilen konum, uygulama dizini veya bir alt dizin ile kısıtlanır. Derlemenin tanımlayıcı bir adı varsa, [ \<codeBase> öğe](../configure-apps/file-schema/runtime/codebase-element.md) bilgisayar üzerinde veya ağ üzerinde herhangi bir konum belirtebilir.  
  
 Yönetilmeyen kod veya COM ile birlikte çalışma uygulamaları için derleme bulurken de benzer kurallar geçerlidir: Derleme birden çok uygulama tarafından paylaşılacaksa, genel derleme önbelleğine yüklenmelidir. Yönetilmeyen kodla kullanılan derlemeler, bir tür kitaplığı olarak dışarı aktarılmalı ve kaydedilmelidir. COM ile birlikte çalışma tarafından kullanılan derlemeler kataloğa kaydedilmelidir, ancak bazı durumlarda bu kayıt otomatik olarak gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Uygulamaları Yapılandırma](../configure-apps/index.md)
- [Yönetilmeyen kodla birlikte çalışma](../interop/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
