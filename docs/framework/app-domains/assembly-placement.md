---
title: Derleme Yerleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6281a0f68fa0ce81b4763d8d0e8f17b47771d2ff
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053210"
---
# <a name="assembly-placement"></a>Derleme Yerleştirme
Çoğu .NET Framework uygulaması için, uygulamayı oluşturan derlemeleri uygulama dizininde, uygulama dizininin bir alt dizininde veya genel derleme önbelleğinde (derleme paylaşılıyorsa) bulursunuz. Bir yapılandırma dosyasındaki [ \<codebase > öğesini](../configure-apps/file-schema/runtime/codebase-element.md) kullanarak ortak dil çalışma zamanının bir derlemeyi aradığı yeri geçersiz kılabilirsiniz. Derleme tanımlayıcı bir ada sahip değilse, [ \<codebase > öğesi](../configure-apps/file-schema/runtime/codebase-element.md) kullanılarak belirtilen konum, uygulama dizini veya bir alt dizin ile kısıtlanır. Derlemenin tanımlayıcı bir adı varsa, [ \<codebase > öğesi](../configure-apps/file-schema/runtime/codebase-element.md) bilgisayar üzerinde veya bir ağ üzerinde herhangi bir konumu belirtebilir.  
  
 Yönetilmeyen kod veya COM ile birlikte çalışma uygulamaları için derleme bulurken de benzer kurallar geçerlidir: Derleme birden çok uygulama tarafından paylaşılacaksa, genel derleme önbelleğine yüklenmelidir. Yönetilmeyen kodla kullanılan derlemeler, bir tür kitaplığı olarak dışarı aktarılmalı ve kaydedilmelidir. COM ile birlikte çalışma tarafından kullanılan derlemeler kataloğa kaydedilmelidir, ancak bazı durumlarda bu kayıt otomatik olarak gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Uygulamaları Yapılandırma](../configure-apps/index.md)
- [Yönetilmeyen kodla birlikte çalışma](../interop/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
