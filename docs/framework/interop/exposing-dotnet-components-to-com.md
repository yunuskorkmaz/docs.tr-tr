---
title: .NET bileşenlerini COM 'a gösterme
description: .NET bileşenlerini COM 'a sunun. Birlikte çalışma için .NET türlerini niteleyin. Birlikte çalışma özniteliklerini uygulayın. COM için bir derlemeyi paketleyin. COM 'dan yönetilen bir tür kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: dc808f3e8d6bd89ba979d43e5b4ec9d787bd09b1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545265"
---
# <a name="exposing-net-components-to-com"></a>.NET bileşenlerini COM 'a gösterme

.NET türü yazmak ve yönetilmeyen koddan Bu türün kullanılması, geliştiriciler için ayrı etkinliklerdir. Bu bölümde, COM istemcileriyle birlikte çalışan yönetilen kod yazmak için çeşitli ipuçları açıklanmaktadır:

- [Birlikte çalışma için .NET türlerini niteleme](../../standard/native-interop/qualify-net-types-for-interoperation.md).

     COM 'da kullanıma sunmak istediğiniz tüm yönetilen türler, Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır. Türler, COM ile çağrılabilen tek Oluşturucu olan ortak parametresiz bir oluşturucuya sahip olmalıdır.

- [Birlikte çalışma öznitelikleri uygulanıyor](../../standard/native-interop/apply-interop-attributes.md).

     Yönetilen kod içindeki özel öznitelikler bir bileşenin birlikte çalışabilirliğini artırabilir.

- [Com için bir derleme paketleniyor](packaging-an-assembly-for-com.md).

     COM geliştiricileri, derlemelerinizi başvurma ve dağıtma konusunda yer alan adımları özetlemenizi gerektirebilir.

 Ayrıca, bu bölüm bir COM istemcisinden yönetilen bir tür tüketme ile ilgili görevleri tanımlar.

## <a name="to-consume-a-managed-type-from-com"></a>COM 'dan yönetilen bir tür kullanmak için

1. [DERLEMELERI com Ile kaydedin](registering-assemblies-with-com.md).

     Bir derlemedeki türlerin (ve tür kitaplıklarının) tasarım zamanında kayıtlı olması gerekir. Bir yükleyici derlemeyi KAYDETMEZSE, COM geliştiricilerine Regasm.exe kullanmalarını söyleyin.

2. [Com 'dan .net türlerine başvurun](how-to-reference-net-types-from-com.md).

     COM geliştiricileri, günümüzde kullandıkları aynı araçları ve teknikleri kullanarak bir derlemedeki türlere başvurabilir.

3. [.Net nesnesi çağırma](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).

     COM geliştiricileri, hiçbir yönetilmeyen türdeki yöntemleri çağırdıkları şekilde .NET nesnesi üzerinde Yöntemler çağırabilirler. Örneğin, COM **Cocreateınstance** API 'si .net nesnelerini etkinleştirir.

4. [Com erişimi için bir uygulamayı dağıtın](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).

     Tanımlayıcı adlı bir derleme, genel derleme önbelleğine yüklenebilir ve yayımcısından imza gerektirir. Tanımlayıcı olarak adlandırılmış olmayan derlemeler istemcinin uygulama dizininde yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kod ile Birlikte Çalışma](index.md)
- [COM Birlikte Çalışma Örneği: COM İstemcisi ve .NET Sunucusu](com-interop-sample-com-client-and-net-server.md)
