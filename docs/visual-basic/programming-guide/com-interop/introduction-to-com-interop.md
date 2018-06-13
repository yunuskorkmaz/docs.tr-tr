---
title: COM Birlikte Çalışma'ya Giriş (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 639b621215f25bc1042274a92a21fca2985e5918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644405"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Birlikte Çalışma'ya Giriş (Visual Basic)
Bileşen Nesne Modeli (COM) diğer bileşenler ve konak uygulamaların işlevselliğini kullanıma nesneyi sağlar. COM nesneleri Windows yıllardır programlama için temel olsa da, Ortak Dil Çalışma Zamanı Modülü (CLR) tasarlanmış uygulamaları birçok avantaj sunar.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulamaları sonunda olanlar com ile geliştirilen değiştirir O zamana kadar kullanın veya Visual Studio kullanarak COM nesneleri oluşturma gerekebilir. COM birlikte çalışabilirliği veya *COM birlikte çalışma*, geçiş sırasında var olan COM nesneleri kullanmanıza olanak tanır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kendi hızınıza.  
  
 Kullanarak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] COM bileşenlerini oluşturmak için Kayıtsız COM birlikte çalışma kullanabilirsiniz. Bu, birden fazla sürümü bir bilgisayarda yüklendiğinde ve son kullanıcılar XCOPY veya FTP uygulamanız kendi bilgisayarında uygun bir dizine kopyalamak için burada çalıştırılması kullanın sağlar hangi DLL sürümü etkin denetlemenize olanak tanır. Daha fazla bilgi için bkz: [Kayıtsız COM birlikte çalışma](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Yönetilen kod ve veriler  
 Kod geliştirilen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] olarak adlandırılır *yönetilen kod*ve CLR tarafından kullanılan meta veriler içeriyor. Tarafından kullanılan veri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulamaları çağrılır *yönetilen veri* ayırma ve bellek geri kazanma ve gerçekleştirme tür denetimi gibi çalışma zamanı veri ilişkili görevler yönetir olduğundan. Varsayılan olarak, Visual Basic .NET yönetilen kod ve veri kullanır ancak yönetilmeyen kod ve birlikte çalışma derlemeleri (daha sonra bu sayfada açıklanan) kullanarak COM nesneleri verilerini erişebilirsiniz.  
  
## <a name="assemblies"></a>Derlemeler  
 Bir derlemeyi birincil yapı bloğudur bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama. Yerleşik sürümü tutulan ve bir veya daha fazla dosyaları içeren bir tek uygulama birim olarak dağıtılan işlevselliği koleksiyonudur. Her derlemenin derleme bildirimi içerir.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Tür kitaplıklarını ve derleme bildirimleri  
 Tür kitaplıkları üye adları ve veri türleri gibi COM nesnelerin özelliklerini açıklar. Derleme bildirimlerinin gerçekleştirmek için aynı işlevi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulamalar. Bunlar aşağıdakiler hakkında bilgi içermektedir:  
  
-   Derleme kimliği, sürüm, kültür ve dijital imza.  
  
-   Derleme uygulama yapmak dosyalar.  
  
-   Türleri ve derlemeyi oluşturan kaynaklar. Bu, ondan dışarı içerir.  
  
-   Derleme zamanı bağımlılıkları diğer derlemeleri.  
  
-   Derlemesi düzgün şekilde çalışması gerekli izinler.  
  
 Derlemeler ve derleme bildirimleri hakkında daha fazla bilgi için bkz: [derlemeler ve genel derleme önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>İçeri ve dışarı aktarma tür kitaplıkları  
 Visual Studio tür kitaplığından bilgileri içe aktarmanıza izin verir Tlbimp, bir yardımcı içeren bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama. Tlbexp yardımcı programını kullanarak derlemelerden tür kitaplıklarının oluşturabilir.  
  
 Tlbimp ve Tlbexp hakkında daha fazla bilgi için bkz: [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md) ve [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri  
 Birlikte çalışma derlemeleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] köprüsü arasında yönetilen ve yönetilmeyen derlemeleri kod, eşleme COM Nesne üyeleri eşdeğerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yönetilen üyeler. Visual Basic .NET tarafından oluşturulan birlikte çalışma derlemeleri birçok birlikte çalışabilirlik hazırlama gibi COM nesneleri ile çalışma ayrıntılarını işler.  
  
## <a name="interoperability-marshaling"></a>Birlikte çalışabilirlik hazırlama  
 Tüm [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulamaları kullanılan programlama diline bakılmaksızın nesneleri birlikte çalışabilirliği sağlamak genel türleri kümesini paylaşır. Parametreler ve dönüş değerleri COM nesnelerinin bazen yönetilen kodda kullanılanlardan farklı veri türlerini kullanın. *Birlikte çalışabilirlik hazırlama* COM nesneleri gelen ve giden taşırken paketleme parametreler ve dönüş değerleri eşdeğer veri türlerine işlemidir. Daha fazla bilgi için bkz: [birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)  
 [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Birlikte Çalışma için Hazırlama](../../../framework/interop/interop-marshaling.md)  
 [Kayıtsız COM Birlikte Çalışma](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
