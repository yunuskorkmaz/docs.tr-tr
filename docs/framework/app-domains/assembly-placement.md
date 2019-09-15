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
ms.openlocfilehash: 829aa80169319b67a8cc5ee39fee9214cd4fcbce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971633"
---
# <a name="assembly-placement"></a>Derleme Yerleştirme
Çoğu .NET Framework uygulaması için, uygulamayı oluşturan derlemeleri uygulama dizininde, uygulama dizininin bir alt dizininde veya genel derleme önbelleğinde (derleme paylaşılıyorsa) bulursunuz. Bir yapılandırma dosyasındaki [ \<codebase > öğesini](../../framework/configure-apps/file-schema/runtime/codebase-element.md) kullanarak ortak dil çalışma zamanının bir derlemeyi aradığı yeri geçersiz kılabilirsiniz. Derleme tanımlayıcı bir ada sahip değilse, [ \<codebase > öğesi](../../framework/configure-apps/file-schema/runtime/codebase-element.md) kullanılarak belirtilen konum, uygulama dizini veya bir alt dizin ile kısıtlanır. Derlemenin tanımlayıcı bir adı varsa, [ \<codebase > öğesi](../../framework/configure-apps/file-schema/runtime/codebase-element.md) bilgisayar üzerinde veya bir ağ üzerinde herhangi bir konumu belirtebilir.  
  
 Yönetilmeyen kod veya COM ile birlikte çalışma uygulamaları için derleme bulurken de benzer kurallar geçerlidir: Derleme birden çok uygulama tarafından paylaşılacaksa, genel derleme önbelleğine yüklenmelidir. Yönetilmeyen kodla kullanılan derlemeler, bir tür kitaplığı olarak dışarı aktarılmalı ve kaydedilmelidir. COM ile birlikte çalışma tarafından kullanılan derlemeler kataloğa kaydedilmelidir, ancak bazı durumlarda bu kayıt otomatik olarak gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Uygulamaları Yapılandırma](../../../docs/framework/configure-apps/index.md)
- [Yönetilmeyen kodla birlikte çalışma](../../../docs/framework/interop/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
