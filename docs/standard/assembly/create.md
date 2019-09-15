---
title: Derlemeler oluştur
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2dda45cca182d75bc77916cdf862ada9faead9ec
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973308"
---
# <a name="create-assemblies"></a>Derlemeler oluştur

Visual Studio gibi bir IDE veya Windows SDK tarafından sunulan derleyiciler ve araçlar aracılığıyla tek dosyalı veya çok dosyalı derlemeler oluşturabilirsiniz. En basit derleme basit bir ada sahip tek bir dosyadır ve tek bir uygulama etki alanına yüklenir. Bu derlemeye, uygulama dizini dışındaki diğer derlemeler tarafından başvurulamaz ve sürüm denetimi çalışmıyor. Derlemeden oluşan uygulamayı kaldırmak için, bulunduğu dizini silmeniz yeterlidir. Birçok geliştirici için, bu özelliklere sahip bir derleme, bir uygulamanın dağıtılması için gerekli olan bir derlemedir.

Çeşitli kod modüllerinden ve kaynak dosyalarından çok dosyalı bir derleme oluşturabilirsiniz. Ayrıca, birden çok uygulama tarafından paylaşılabilen bir derleme da oluşturabilirsiniz. Paylaşılan bir derlemenin tanımlayıcı adı olması ve genel derleme önbelleğinde dağıtılması gerekir.

Aşağıdaki faktörlere bağlı olarak kod modüllerini ve kaynakları derlemeler halinde gruplandırırken çeşitli seçenekleriniz vardır:

- Sürüm Oluşturma

     Aynı sürüm bilgisine sahip olması gereken grup modülleri.

- Dağıtım

     Dağıtım modelinizi destekleyen grup kodu modülleri ve kaynakları.

- Pencereleri

     Bir amaç için mantıksal olarak birlikte kullanılabilen modülleri gruplandırın. Örneğin, program bakımı için seyrek kullanılan türler ve sınıflardan oluşan bir derleme aynı derlemeye yerleştirilebilir. Ayrıca, birden çok uygulamayla paylaşmayı planladığınız türler bir derlemede gruplandırılmalıdır ve derleme tanımlayıcı bir adla imzalanmalıdır.

- Güvenlik

     Aynı güvenlik izinleri gerektiren türleri içeren modülleri gruplandırın.

- Kapsamlar

     Görünürlüğü aynı derleme ile kısıtlanması gereken türler içeren modülleri gruplandırın.

Yönetilmeyen COM uygulamaları için ortak dil çalışma zamanı derlemeleri kullanılabilir hale getirmeyle ilgili özel durumlar vardır. Yönetilmeyen kodla çalışma hakkında daha fazla bilgi için bkz. [BILEŞENLERI com 'da .NET Framework kullanıma](../../framework/interop/exposing-dotnet-components-to-com.md)sunma.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş kod içeren program](program.md)
- [Derleme sürümü oluşturma](versioning.md)
- [Nasıl yapılır: Tek dosya derlemesi oluşturma](../../framework/app-domains/build-single-file-assembly.md)
- [Nasıl yapılır: Çoklu dosya derlemesi oluşturma](../../framework/app-domains/build-multifile-assembly.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Çoklu dosya derlemeleri](../../framework/app-domains/multifile-assemblies.md)
