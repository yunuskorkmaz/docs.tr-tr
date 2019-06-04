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
ms.openlocfilehash: 00347b295eb5d9a092fb817e75f852f16004bb87
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489270"
---
# <a name="deploying-an-interop-application"></a>Birlikte Çalışma Uygulamasını Dağıtma
Birlikte çalışma uygulamasını genellikle bir .NET istemci bütünleştirilmiş kodu içeren bir veya daha fazla birlikte çalışma derlemelerini temsil eden ayrı bir COM tür kitaplığı ve COM bileşenlerini bir veya daha fazla kayıtlı. Visual Studio ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] bölümünde açıklandığı gibi içeri aktarma ve birlikte çalışma derlemesine bir tür kitaplığına dönüştürme için araçlar sağlar [bir tür kitaplığını derleme olarak içeri aktarma](importing-a-type-library-as-an-assembly.md). Birlikte çalışma uygulamasını dağıtmak için iki yolu vardır:  
  
- Gömülü birlikte çalışma türleri kullanarak: .NET Framework 4 ile başlayarak, derleyicinin tür bilgilerini birlikte çalışma bütünleştirilmiş kod yürütülebilir dosyanın içine gömmek için bildirebilirsiniz. Derleyici, uygulamanızın kullandığı tür bilgilerini katıştırır. Uygulamanızla birlikte çalışma derlemesi dağıtmak gerekmez. Önerilen yöntem budur.  
  
- Birlikte çalışma derlemelerini dağıtarak: Standart bir birlikte çalışma derlemesine başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesi uygulamanızla dağıtılması gerekir. Bu tekniği kullanır ve özel bir COM bileşeni kullanmıyorsanız, her zaman, yönetilen kodda birleştirmek istiyorsanız COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesi (PIA) başvuru. Üretme ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemelerini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Gömülü birlikte çalışma türleri kullanıyorsanız, bunları olabildiğince sade ve dağıtım. Yapmanız gereken özel bir şey yoktur. Bu makalenin geri kalanında, uygulamanızla birlikte çalışma derlemelerini dağıtma senaryoları açıklar.  
  
## <a name="deploying-interop-assemblies"></a>Birlikte çalışma derlemelerini dağıtma  
 Derlemelerin tanımlayıcı adları olabilir. Tanımlayıcı adlı bütünleştirilmiş kod benzersiz bir kimlik sağlar yayımcının ortak anahtarı içerir. Tarafından üretilen derlemelerin [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) kullanarak yayımcı tarafından imzalanmış **/keyfile** seçeneği. İmzalı derlemeler genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz. İmzasız derlemeler kullanıcının makinesine özel derlemeler yüklenmesi gerekir.  
  
### <a name="private-assemblies"></a>Özel derlemeler  
 Özel olarak kullanılacak bir derlemeyi yüklemek için hem uygulama yürütülebilir hem de içeri aktarılan COM türlerini içeren birlikte çalışma bütünleştirilmiş kod aynı dizin yapısında yüklenmelidir. Ayrı uygulama dizinlerde bulunan Client1.exe ve Client2.exe, tarafından özel olarak kullanılmak üzere, işaretsiz bir birlikte çalışma derlemesi aşağıda gösterilmiştir. Bu örnekte LOANLib.dll çağrılır, birlikte çalışma derlemesi iki kez yüklenir.  
  
 ![Dizin yapısını ve Windows kayıt defteri](./media/deploying-an-interop-application/com-private-deployment.gif "özel bir dağıtım için dizin yapısını ve kayıt defteri girdileri")  
  
 Uygulamayla ilişkili tüm COM bileşenlerini Windows kayıt defterinde yüklenmesi gerekir. Client1.exe ve çizimdeki Client2.exe farklı bilgisayarlarda yüklüyse, her iki bilgisayarda COM bileşenlerini kaydetmeniz gerekir.  
  
### <a name="shared-assemblies"></a>Paylaşılan derlemeler  
 Birden çok uygulama tarafından paylaşılan derlemeleri genel bütünleştirilmiş kod önbelleğine merkezi bir depoda yüklü olması gerekir. .NET istemcileri imzalanır ve genel derleme önbelleğinde yüklü birlikte çalışma derlemesi aynı kopyasını erişebilir. Üretme ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemelerini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Birlikte Çalışma Projesi Derleme](compiling-an-interop-project.md)
