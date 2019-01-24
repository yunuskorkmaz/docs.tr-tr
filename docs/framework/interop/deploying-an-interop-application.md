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
ms.openlocfilehash: 8e74e4784d295e46972e10c5b9e1d4cc4bafa944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496773"
---
# <a name="deploying-an-interop-application"></a>Birlikte Çalışma Uygulamasını Dağıtma
Birlikte çalışma uygulamasını genellikle bir .NET istemci bütünleştirilmiş kodu içeren bir veya daha fazla birlikte çalışma derlemelerini temsil eden ayrı bir COM tür kitaplığı ve COM bileşenlerini bir veya daha fazla kayıtlı. Visual Studio ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] bölümünde açıklandığı gibi içeri aktarma ve birlikte çalışma derlemesine bir tür kitaplığına dönüştürme için araçlar sağlar [bir tür kitaplığını derleme olarak içeri aktarma](importing-a-type-library-as-an-assembly.md). Birlikte çalışma uygulamasını dağıtmak için iki yolu vardır:  
  
-   Gömülü birlikte çalışma türleri kullanarak: İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], derleyicinin tür bilgilerini birlikte çalışma bütünleştirilmiş kod yürütülebilir dosyanın içine gömmek için bildirebilirsiniz. Derleyici, uygulamanızın kullandığı tür bilgilerini katıştırır. Uygulamanızla birlikte çalışma derlemesi dağıtmak gerekmez. Önerilen yöntem budur.  
  
-   Birlikte çalışma derlemelerini dağıtarak: Standart bir birlikte çalışma derlemesine başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesi uygulamanızla dağıtılması gerekir. Bu tekniği kullanır ve özel bir COM bileşeni kullanmıyorsanız, her zaman, yönetilen kodda birleştirmek istiyorsanız COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesi (PIA) başvuru. Üretme ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemelerini](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Gömülü birlikte çalışma türleri kullanıyorsanız, bunları olabildiğince sade ve dağıtım. Yapmanız gereken özel bir şey yoktur. Bu makalenin geri kalanında, uygulamanızla birlikte çalışma derlemelerini dağıtma senaryoları açıklar.  
  
## <a name="deploying-interop-assemblies"></a>Birlikte çalışma derlemelerini dağıtma  
 Derlemelerin tanımlayıcı adları olabilir. Tanımlayıcı adlı bütünleştirilmiş kod benzersiz bir kimlik sağlar yayımcının ortak anahtarı içerir. Tarafından üretilen derlemelerin [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) kullanarak yayımcı tarafından imzalanmış **/keyfile** seçeneği. İmzalı derlemeler genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz. İmzasız derlemeler kullanıcının makinesine özel derlemeler yüklenmesi gerekir.  
  
### <a name="private-assemblies"></a>Özel derlemeler  
 Özel olarak kullanılacak bir derlemeyi yüklemek için hem uygulama yürütülebilir hem de içeri aktarılan COM türlerini içeren birlikte çalışma bütünleştirilmiş kod aynı dizin yapısında yüklenmelidir. Ayrı uygulama dizinlerde bulunan Client1.exe ve Client2.exe, tarafından özel olarak kullanılmak üzere, işaretsiz bir birlikte çalışma derlemesi aşağıda gösterilmiştir. Bu örnekte LOANLib.dll çağrılır, birlikte çalışma derlemesi iki kez yüklenir.  
  
 ![Dizin yapısını ve Windows kayıt defteri](media/comdeployprivate.gif "comdeployprivate")  
Özel bir dağıtım için dizin yapısını ve kayıt defteri girdileri  
  
 Uygulamayla ilişkili tüm COM bileşenlerini Windows kayıt defterinde yüklenmesi gerekir. Client1.exe ve çizimdeki Client2.exe farklı bilgisayarlarda yüklüyse, her iki bilgisayarda COM bileşenlerini kaydetmeniz gerekir.  
  
### <a name="shared-assemblies"></a>Paylaşılan derlemeler  
 Birden çok uygulama tarafından paylaşılan derlemeleri genel bütünleştirilmiş kod önbelleğine merkezi bir depoda yüklü olması gerekir. .NET istemcileri imzalanır ve genel derleme önbelleğinde yüklü birlikte çalışma derlemesi aynı kopyasını erişebilir. Üretme ve birincil birlikte çalışma derlemeleri kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemelerini](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [Birlikte Çalışma Projesi Derleme](compiling-an-interop-project.md)
