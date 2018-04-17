---
title: Birlikte Çalışma Uygulamasını Dağıtma
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8271a30d2258214defd5a15816813875cf594c8b
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-an-interop-application"></a>Birlikte Çalışma Uygulamasını Dağıtma
Birlikte çalışma uygulamasını genellikle bir .NET istemci derlemesi içerir, ayrı COM temsil eden bir veya daha fazla birlikte çalışma derlemeleri tür kitaplıkları ve COM bileşenlerini bir veya daha fazla kayıtlı. Visual Studio ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] almak ve birlikte çalışabilirlik bütünleştirilmiş bir tür kitaplığı dönüştürmek için Araçlar'da anlatıldığı gibi sağlamak [tür kitaplığını derleme olarak içeri aktarma](importing-a-type-library-as-an-assembly.md). Birlikte çalışma uygulamasını dağıtmak için iki yol vardır:  
  
-   Katıştırılmış birlikte çalışma türlerini kullanarak: itibaren [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yürütülebilir dosyanın birlikte çalışma derlemeye tür bilgilerini katıştırma görevlendirin. Derleyici, uygulamanızın kullandığı türü bilgilerini katıştırır. Uygulamanız ile birlikte çalışma derlemeyi dağıtmanız gerekmez. Önerilen yöntem budur.  
  
-   Birlikte çalışma derlemeleri dağıtarak: birlikte çalışma derlemesi için standart bir başvuru oluşturabilirsiniz. Bu durumda, uygulamanız ile birlikte çalışma derlemesi dağıtılmalıdır. Bu yöntem uygulamadığınız ve özel bir COM bileşeni kullanmıyorsanız, her zaman yönetilen kodunuzda birleştirmek istiyorsanız COM bileşeni yazarı tarafından yayımlanan birincil birlikte çalışma derlemesi (PIA) başvuru. Oluşturan ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz: [birincil birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Katıştırılmış birlikte çalışma türlerini kullanın, dağıtım basit ve kolay olur. Yapmanız gereken özel bir şey yoktur. Bu makalenin geri kalanında uygulamanız ile birlikte çalışma derlemeleri dağıtma senaryoları açıklanmıştır.  
  
## <a name="deploying-interop-assemblies"></a>Birlikte çalışma derlemeleri dağıtma  
 Derlemelerin tanımlayıcı adlar sağlayabilirsiniz. Tanımlayıcı adlı bir derleme benzersiz bir kimliği sağlar publisher'ın ortak anahtarı içerir. Tarafından üretilen derlemeleri [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) kullanarak yayımcı tarafından imzalanmış **/keyfile** seçeneği. İmzalı derlemeler genel derleme önbelleğine yükleyebilirsiniz. İmzasız derlemeler kullanıcının makinesinde özel derlemeler yüklenmesi gerekir.  
  
### <a name="private-assemblies"></a>Özel derlemeler  
 Özel olarak kullanılacak bir derlemeyi yüklemek için hem uygulama yürütülebilir dosyasının hem de içeri aktarılan COM türlerini içeren birlikte çalışma derlemenin aynı dizin yapısını yüklenmelidir. Aşağıdaki çizimde imzalanmamış birlikte çalışma bir derlemeyi ayrı uygulama dizinlerde bulunan Client1.exe ve Client2.exe, tarafından özel olarak kullanılmak üzere gösterir. Bu örnekte LOANLib.dll çağrılır, birlikte çalışma derlemesi iki kez yüklenir.  
  
 ![Dizin yapısını ve Windows kayıt defteri](media/comdeployprivate.gif "comdeployprivate")  
Özel bir dağıtım için dizin yapısını ve kayıt defteri girdileri  
  
 Uygulama ile ilişkili tüm COM bileşenlerini Windows Kayıt Defteri'nde yüklenmesi gerekir. Client1.exe ve Client2.exe çizimdeki farklı bilgisayarlarda yüklü değilse, her iki bilgisayarda COM bileşenlerini kaydetmeniz gerekir.  
  
### <a name="shared-assemblies"></a>Paylaşılan derlemeler  
 Birden çok uygulama tarafından paylaşılan derlemeleri genel derleme önbelleğine merkezi bir depoda yüklü olmalıdır. .NET istemcileri imzalanmış ve genel derleme önbelleğinde yüklü birlikte çalışma derlemesi'nın aynı kopyasını erişebilir. Oluşturan ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz: [birincil birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
 [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)  
 [Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [Birlikte Çalışma Projesi Derleme](compiling-an-interop-project.md)
