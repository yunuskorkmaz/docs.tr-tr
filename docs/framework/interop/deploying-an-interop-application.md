---
title: Birlikte Çalışma Uygulamasını Dağıtma
description: Genellikle .NET istemci derlemesi, farklı COM tür kitaplıklarının birlikte çalışma derlemeleri ve kayıtlı COM bileşenleri bulunan bir birlikte çalışma uygulaması dağıtın.
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
ms.openlocfilehash: 744307d4175d151d07acbedd5815e538307c8973
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617489"
---
# <a name="deploying-an-interop-application"></a>Birlikte Çalışma Uygulamasını Dağıtma
Birlikte çalışabilirlik uygulaması genellikle .NET istemci derlemesini, farklı COM tür kitaplıklarını temsil eden bir veya daha fazla birlikte çalışma derlemesini ve bir veya daha fazla kayıtlı COM bileşenini içerir. Visual Studio ve Windows SDK, bir tür kitaplığını [derleme olarak Içeri aktarma](importing-a-type-library-as-an-assembly.md)konusunda anlatıldığı gibi bir tür kitaplığını içeri ve dışarı aktarma derlemesine dönüştürmek için araçlar sağlar. Birlikte çalışabilirlik uygulamasını dağıtmanın iki yolu vardır:  
  
- Gömülü birlikte çalışma türlerini kullanarak: .NET Framework 4 ' ten başlayarak, derleyicinin tür bilgilerini yürütülebilir bir derlemeden çalıştırılabilire eklemesini isteyebilirsiniz. Derleyici yalnızca uygulamanızın kullandığı tür bilgilerini katıştırır. Birlikte çalışma derlemesini uygulamanızla birlikte dağıtmanız gerekmez. Önerilen yöntem budur.  
  
- Birlikte çalışma bütünleştirilmiş kodlarını dağıtarak: bir birlikte çalışma derlemesine standart bir başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir. Bu tekniği kullandıysanız ve özel bir COM bileşeni kullanmıyorsanız, her zaman yönetilen kodunuzda birleştirmek istediğiniz COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesine (PIA) başvurun. Birincil birlikte çalışma derlemelerini üretme ve kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Katıştırılmış birlikte çalışma türleri kullanıyorsanız, dağıtım basittir ve basittir. Yapmanız gereken özel bir şey yoktur. Bu makalenin geri kalanında, birlikte çalışma derlemelerini uygulamanızla dağıtmaya yönelik senaryolar açıklanmaktadır.  
  
## <a name="deploying-interop-assemblies"></a>Birlikte çalışma derlemelerini dağıtma  
 Derlemeler tanımlayıcı adlara sahip olabilir. Tanımlayıcı adlı bir derleme, yayımcının ortak anahtarını içerir ve bu da benzersiz bir kimlik sağlar. [Tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) tarafından üretilen derlemeler, **/keyfile** seçeneği kullanılarak yayımcı tarafından imzalanabilir. İmzalı derlemeleri genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz. İmzasız derlemelerin Kullanıcı makinesine özel derlemeler olarak yüklenmesi gerekir.  
  
### <a name="private-assemblies"></a>Özel derlemeler  
 Özel olarak kullanılacak bir derlemeyi yüklemek için, hem uygulama yürütülebilir dosyası hem de içeri aktarılan COM türlerini içeren birlikte çalışma derlemesi aynı dizin yapısında yüklü olmalıdır. Aşağıdaki çizimde, ayrı uygulama dizinlerinde bulunan Client1.exe ve Client2.exe özel olarak kullanılacak işaretsiz bir birlikte çalışma derlemesi gösterilmektedir. Bu örnekte LOANLib.dll olarak adlandırılan birlikte çalışma derlemesi iki kez yüklenir.  
  
 ![Dizin yapısı ve Windows kayıt defteri](./media/deploying-an-interop-application/com-private-deployment.gif "Özel dağıtım için dizin yapısı ve kayıt defteri girişleri")  
  
 Uygulamayla ilişkili tüm COM bileşenlerinin Windows kayıt defterine yüklenmesi gerekir. Çizimdeki Client1.exe ve Client2.exe farklı bilgisayarlara yüklenirse, COM bileşenlerini her iki bilgisayara da kaydetmeniz gerekir.  
  
### <a name="shared-assemblies"></a>Paylaşılan derlemeler  
 Birden çok uygulama tarafından paylaşılan derlemelerin genel derleme önbelleği adlı merkezi bir depoya yüklenmesi gerekir. .NET istemcileri, imzalanmış ve genel derleme önbelleğinde yüklü olan birlikte çalışma derlemesinin aynı kopyasına erişebilir. Birincil birlikte çalışma derlemelerini üretme ve kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Birlikte Çalışma Projesi Derleme](compiling-an-interop-project.md)
