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
ms.openlocfilehash: 2d90b3c23af39125d888824dbfabf798a3e73985
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218742"
---
# <a name="exposing-net-framework-components-to-com"></a>.NET Framework Bileşenlerini COM'da Gösterme
.NET türüne yazma ve bu tür, yönetilmeyen koddan kullanan geliştiriciler için ayrı etkinliklerdir. Bu bölümde, COM istemcileri ile birlikte çalışan yönetilen kod yazma için bazı ipuçları açıklanmaktadır:  
  
-   [Birlikte çalışma için .NET türlerini niteleme](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Tüm yönetilen türleri, yöntemleri, özellikleri, alanları ve COM öğesine göstermek istediğiniz olayların ortak olması gerekir. Türler, COM içinden çağrılabilen tek Oluşturucu olan bir genel varsayılan oluşturucuya sahip olmalıdır  
  
-   [Birlikte çalışma özniteliklerini uygulama](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Yönetilen kod içinde özel öznitelikler, bir bileşenin birlikte çalışabilirliği geliştirebilirsiniz.  
  
-   [COM için derlemeyi paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     COM geliştiriciler, başvuru ve bütünleştirilmiş kodlarınızı dağıtma adımlarını özetleyen gerektirebilir.  
  
 Ayrıca, bu bölümü, COM istemciden yönetilen bir tür kullanan için ilgili görevleri tanımlar.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Yönetilen bir COM türünden kullanma  
  
1.  [Derlemeleri COM ile kaydetme](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Tasarım zamanında bir derleme (ve tür kitaplıklarını) türlerinde kayıtlı olması gerekir. Bir yükleyici bütünleştirilmiş kod kaydedilmiyorsa COM geliştiriciler Regasm.exe isteyin.  
  
2.  [Com'dan .NET türlerine başvurma](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Aynı araçları ve bugün kullandıkları teknikleri kullanarak derlemedeki türleri COM geliştiriciler başvurabilirsiniz.  
  
3.  [Bir .NET nesnesini çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).  
  
     COM geliştiriciler, bunlar herhangi bir yönetilmeyen türü üzerinde yöntemleri çağırmak aynı şekilde .NET nesne üzerinde yöntemleri çağırabilir. Örneğin, COM **CoCreateInstance** API .NET nesneleri etkinleştirir.  
  
4.  [COM erişimi için bir uygulamayı dağıtmak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).  
  
     Bir katı adlı derleme genel derleme önbelleğinde yüklü ve yayımcısını imzasının gerektirir. İstemci uygulama dizininde olmayan kesin adlı derlemeler yüklenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)
- [COM birlikte çalışma örneği: COM istemcisi ve .NET sunucusu](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
