---
title: Derleme oluşturma
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740512"
---
# <a name="create-assemblies"></a>Derleme oluşturma

Visual Studio gibi bir IDE veya Windows SDK tarafından sağlanan derleyiciler ve araçlar kullanarak tek dosyalı veya çok dosyalı derlemeler oluşturabilirsiniz. En basit derleme, basit bir ada sahip olan ve tek bir uygulama etki alanına yüklenen tek bir dosyadır. Bu derleme, uygulama dizini dışındaki diğer derlemeler tarafından başvurulamaz ve sürüm denetiminden geçmez. Derlemeden oluşan uygulamayı kaldırmak için, bulunduğu yerdeki dizini silmeniz yeterlidir. Birçok geliştirici için, bu özelliklere sahip bir derleme, bir uygulamayı dağıtmak için gereken tek şeydir.

Çeşitli kod modüllerinden ve kaynak dosyalarından çok dosyalı bir derleme oluşturabilirsiniz. Ayrıca, birden çok uygulama tarafından paylaşılabilir bir derleme oluşturabilirsiniz. Paylaşılan bir derlemenin güçlü bir adı olmalıdır ve genel derleme önbelleğinde dağıtılabilir.

Kod modüllerini ve kaynaklarını aşağıdaki etkenlere bağlı olarak derlemeler halinde gruplandırmak için birkaç seçeneğiniz vardır:

- Sürüm oluşturma

     Aynı sürüm bilgilerine sahip olması gereken modülleri gruplandırma.

- Dağıtım

     Dağıtım modelinizi destekleyen kod modüllerini ve kaynakları gruplandırma.

- Yeniden kullanma

     Modülleri mantıksal olarak bir amaç için birlikte kullanılabiliyorsa gruplayın. Örneğin, program bakımı için seyrek kullanılan tür ve sınıflardan oluşan bir derleme aynı derlemeye konabilir. Buna ek olarak, birden çok uygulamayla paylaşmayı istediğiniz türler bir derleme halinde gruplandırılmalı ve derleme güçlü bir adla imzalanmalıdır.

- Güvenlik

     Aynı güvenlik izinleri gerektiren türleri içeren modülleri gruplandırma.

- Kapsam

     Görünürlüğü aynı montajla sınırlandırılmalı türleri içeren grupları gruplandırın.

Yönetilmeyen COM uygulamaları için ortak dil çalışma zamanı derlemeleri yaparken özel hususlar vardır. Yönetilmeyen kodla çalışma hakkında daha fazla bilgi için [bkz.](../../framework/interop/exposing-dotnet-components-to-com.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Montaj sürümü](versioning.md)
- [Nasıl yapılı: Tek dosyalı derleme oluşturma](../../framework/app-domains/build-single-file-assembly.md)
- [Nasıl yapılı: Çok dosyalı derleme oluşturma](../../framework/app-domains/build-multifile-assembly.md)
- [Çalışma zamanı derlemeleri nasıl bulur?](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Çok dosyalı derlemeler](../../framework/app-domains/multifile-assemblies.md)
