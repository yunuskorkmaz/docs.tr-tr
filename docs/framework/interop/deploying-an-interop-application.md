---
title: Birlikte Çalışma Uygulamasını Dağıtma
ms.date: 03/30/2017
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
ms.openlocfilehash: 080ef48ade496a55f414b64158a40fe0e551c2aa
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567292"
---
# <a name="deploying-an-interop-application"></a>Birlikte Çalışma Uygulamasını Dağıtma
Birlikte çalışabilirlik uygulaması genellikle .NET istemci derlemesini, farklı COM tür kitaplıklarını temsil eden bir veya daha fazla birlikte çalışma derlemesini ve bir veya daha fazla kayıtlı COM bileşenini içerir. Visual Studio ve Windows SDK, bir tür kitaplığını [derleme olarak Içeri aktarma](importing-a-type-library-as-an-assembly.md)konusunda anlatıldığı gibi bir tür kitaplığını içeri ve dışarı aktarma derlemesine dönüştürmek için araçlar sağlar. Birlikte çalışabilirlik uygulamasını dağıtmanın iki yolu vardır:  
  
- Gömülü birlikte çalışma türlerini kullanarak: .NET Framework 4 ' ten başlayarak, derleyicinin tür bilgilerini yürütülebilir bir derlemeden çalıştırılabilire katıştırmasını isteyebilirsiniz. Derleyici yalnızca uygulamanızın kullandığı tür bilgilerini katıştırır. Birlikte çalışma derlemesini uygulamanızla birlikte dağıtmanız gerekmez. Önerilen yöntem budur.  
  
- Birlikte çalışma derlemelerini dağıtarak: Birlikte çalışabilirlik derlemesine standart bir başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir. Bu tekniği kullandıysanız ve özel bir COM bileşeni kullanmıyorsanız, her zaman yönetilen kodunuzda birleştirmek istediğiniz COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesine (PIA) başvurun. Birincil birlikte çalışma derlemelerini üretme ve kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Katıştırılmış birlikte çalışma türleri kullanıyorsanız, dağıtım basittir ve basittir. Yapmanız gereken özel bir şey yoktur. Bu makalenin geri kalanında, birlikte çalışma derlemelerini uygulamanızla dağıtmaya yönelik senaryolar açıklanmaktadır.  
  
## <a name="deploying-interop-assemblies"></a>Birlikte çalışma derlemelerini dağıtma  
 Derlemeler tanımlayıcı adlara sahip olabilir. Tanımlayıcı adlı bir derleme, yayımcının ortak anahtarını içerir ve bu da benzersiz bir kimlik sağlar. [Tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) tarafından üretilen derlemeler, **/keyfile** seçeneği kullanılarak yayımcı tarafından imzalanabilir. İmzalı derlemeleri genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz. İmzasız derlemelerin Kullanıcı makinesine özel derlemeler olarak yüklenmesi gerekir.  
  
### <a name="private-assemblies"></a>Özel derlemeler  
 Özel olarak kullanılacak bir derlemeyi yüklemek için, hem uygulama yürütülebilir dosyası hem de içeri aktarılan COM türlerini içeren birlikte çalışma derlemesi aynı dizin yapısında yüklü olmalıdır. Aşağıdaki çizimde, ayrı uygulama dizinlerinde bulunan Istemci1. exe ve Istemci2. exe tarafından özel olarak kullanılacak işaretsiz bir birlikte çalışma derlemesi gösterilmektedir. Bu örnekte Krelib. dll olarak adlandırılan birlikte çalışma derlemesi iki kez yüklenir.  
  
 ![Dizin yapısı ve Windows kayıt defteri](./media/deploying-an-interop-application/com-private-deployment.gif "Özel dağıtım Için dizin yapısı ve kayıt defteri girişleri")  
  
 Uygulamayla ilişkili tüm COM bileşenlerinin Windows kayıt defterine yüklenmesi gerekir. Çizimdeki Istemci1. exe ve Istemci2. exe farklı bilgisayarlarda yüklüyse, COM bileşenlerini her iki bilgisayara da kaydetmeniz gerekir.  
  
### <a name="shared-assemblies"></a>Paylaşılan derlemeler  
 Birden çok uygulama tarafından paylaşılan derlemelerin genel derleme önbelleği adlı merkezi bir depoya yüklenmesi gerekir. .NET istemcileri, imzalanmış ve genel derleme önbelleğinde yüklü olan birlikte çalışma derlemesinin aynı kopyasına erişebilir. Birincil birlikte çalışma derlemelerini üretme ve kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Birlikte Çalışma Projesi Derleme](compiling-an-interop-project.md)
