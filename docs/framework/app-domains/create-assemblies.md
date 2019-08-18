---
title: Derlemeler Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314a94be140b392964951299fba2fed4ac7e6e68
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566795"
---
# <a name="creating-assemblies"></a>Derlemeler Oluşturma

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

Yönetilmeyen COM uygulamaları için ortak dil çalışma zamanı derlemeleri kullanılabilir hale geldiğinde özel hususlar yapılmalıdır. Yönetilmeyen kodla çalışma hakkında daha fazla bilgi için bkz. [com 'da .NET Framework bileşenleri gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Bütünleştirilmiş Kod Sürümü Oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)
- [Nasıl yapılır: Tek dosya derlemesi oluşturma](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [Nasıl yapılır: Çoklu dosya derlemesi oluşturma](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)
