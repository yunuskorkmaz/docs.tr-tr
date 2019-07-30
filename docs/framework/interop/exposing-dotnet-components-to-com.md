---
title: .NET Framework Bileşenlerini COM'da Gösterme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c88466df32a4167b2b32a7cc0f64eb306e392611
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629351"
---
# <a name="exposing-net-framework-components-to-com"></a>.NET Framework Bileşenlerini COM'da Gösterme
.NET türü yazmak ve yönetilmeyen koddan Bu türün kullanılması, geliştiriciler için ayrı etkinliklerdir. Bu bölümde, COM istemcileriyle birlikte çalışan yönetilen kod yazmak için çeşitli ipuçları açıklanmaktadır:  
  
- [Birlikte çalışma için .NET türlerini niteleme](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).  
  
     COM 'da kullanıma sunmak istediğiniz tüm yönetilen türler, Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır. Türler, COM ile çağrılabilen tek Oluşturucu olan ortak parametresiz bir oluşturucuya sahip olmalıdır.  
  
- [Birlikte çalışma öznitelikleri uygulanıyor](../../../docs/standard/native-interop/apply-interop-attributes.md).  
  
     Yönetilen kod içindeki özel öznitelikler bir bileşenin birlikte çalışabilirliğini artırabilir.  
  
- [Com için bir derleme paketleniyor](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     COM geliştiricileri, derlemelerinizi başvurma ve dağıtma konusunda yer alan adımları özetlemenizi gerektirebilir.  
  
 Ayrıca, bu bölüm bir COM istemcisinden yönetilen bir tür tüketme ile ilgili görevleri tanımlar.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>COM 'dan yönetilen bir tür kullanmak için  
  
1. [DERLEMELERI com Ile kaydedin](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Bir derlemedeki türlerin (ve tür kitaplıklarının) tasarım zamanında kayıtlı olması gerekir. Bir yükleyici derlemeyi KAYDETMEZSE, COM geliştiricilerine Regasm. exe kullanmayı söyleyin.  
  
2. [Com 'dan .net türlerine başvurun](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     COM geliştiricileri, günümüzde kullandıkları aynı araçları ve teknikleri kullanarak bir derlemedeki türlere başvurabilir.  
  
3. [.Net nesnesi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).  
  
     COM geliştiricileri, hiçbir yönetilmeyen türdeki yöntemleri çağırdıkları şekilde .NET nesnesi üzerinde Yöntemler çağırabilirler. Örneğin, COM **Cocreateınstance** API 'si .net nesnelerini etkinleştirir.  
  
4. [Com erişimi için bir uygulamayı dağıtın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).  
  
     Tanımlayıcı adlı bir derleme, genel derleme önbelleğine yüklenebilir ve yayımcısından imza gerektirir. Tanımlayıcı olarak adlandırılmış olmayan derlemeler istemcinin uygulama dizininde yüklü olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)
- [COM birlikte çalışma örneği: COM Istemcisi ve .NET sunucusu](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
