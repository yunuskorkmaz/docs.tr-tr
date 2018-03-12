---
title: ".NET Framework Bileşenlerini COM'da Gösterme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a1bba04ed410eb195869d2a4bc2868872b04c0d0
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2018
---
# <a name="exposing-net-framework-components-to-com"></a>.NET Framework Bileşenlerini COM'da Gösterme
.NET türü yazma ve bu tür yönetilmeyen koddan kullanan geliştiriciler için ayrı etkinliklerdir. Bu bölümde COM istemcileri ile birlikte çalışan yönetilen kod yazma için birkaç ipuçları açıklanmaktadır:  
  
-   [Birlikte çalışma için .NET türlerini niteleme](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Tüm yönetilen türleri, yöntemler, özellikler, alanları ve COM kullanıma sunmak istediğiniz olayları ortak olması gerekir. Türleri com içinden çağrılabilen tek Oluşturucusu bir ortak varsayılan oluşturucu olmalıdır  
  
-   [Birlikte çalışma özniteliklerini uygulama](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Yönetilen kod içinde özel öznitelikleri bir bileşen birlikte çalışabilirliği geliştirebilirsiniz.  
  
-   [COM için derlemeyi paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     COM geliştiricilerin başvuran ve derlemeleriniz dağıtma adımlarını özetleyen gerektirebilir.  
  
 Ayrıca, bu bölümde bir COM istemciden yönetilen türü tüketen için ilgili görevleri tanımlar.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>COM yönetilen türünden kullanmak için  
  
1.  [Derlemeleri COM ile kaydetme](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Derleme (ve tür kitaplıklarının) türleri tasarım zamanında kayıtlı olması gerekir. Bir yükleyici derleme kaydedilmiyorsa COM geliştiriciler Regasm.exe isteyin.  
  
2.  [Com'dan .NET türlerine başvurma](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Aynı araçları ve bugün kullandıkları teknikleri kullanarak derlemedeki türleri COM geliştiriciler başvurabilirsiniz.  
  
3.  [Bir .NET nesnesini çağıran](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).  
  
     COM geliştiriciler, bunlar üzerinde herhangi bir yönetilmeyen türü yöntemlerini çağıran aynı şekilde .NET nesnesinde yöntemleri çağırabilir. Örneğin, COM **CoCreateInstance** API'si, .NET nesneleri etkinleştirir.  
  
4.  [COM erişim için bir uygulamayı dağıtmak](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).  
  
     Tanımlayıcı adlı bir derleme genel derleme önbelleğinde yüklenebilir ve yayımcısını imzadan gerektirir. İstemci uygulama dizininde değil tanımlayıcı adlı derlemeler yüklenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)  
 [COM Birlikte Çalışma Örneği: COM İstemcisi ve .NET Sunucusu](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
