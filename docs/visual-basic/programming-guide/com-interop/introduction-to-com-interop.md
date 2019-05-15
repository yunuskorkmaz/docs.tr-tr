---
title: COM Birlikte Çalışma'ya Giriş (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 5eb862d75f8870da40af4cd817fa32a3d2781f38
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592726"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Birlikte Çalışma'ya Giriş (Visual Basic)
Bileşen Nesne Modeli (COM) diğer bileşenleri ve uygulamaları barındırmak için işlevselliği kullanıma sunma nesneyi sağlar. COM nesneleri Windows yıllardır programlama için temel kullanımda olsa, Ortak Dil Çalışma Zamanı Modülü (CLR) tasarlanmış uygulamalar birçok avantaj sunar.  
  
 .NET framework uygulamaları sonunda bu COM ile geliştirilen değiştirir O zamana kadar kullanabilir veya Visual Studio kullanarak COM nesneleri oluşturmak gerekebilir. COM birlikte çalışabilirlik veya *COM birlikte çalışma*, var olan COM nesneleri .NET Framework kendi hızınızda geçişi sırasında kullanmanıza olanak tanır.  
  
 COM bileşenleri oluşturmak için .NET Framework kullanarak Kayıtsız COM birlikte çalışma kullanabilirsiniz. Bu, birden fazla sürümünün bir bilgisayarda yüklü ve son kullanıcılar, XCOPY veya FTP uygulamanızı bilgisayarlarında uygun bir dizine kopyalamak için burada çalıştırılabilir kullanma olanak tanır, hangi DLL sürümü etkin denetlemenize olanak tanır. Daha fazla bilgi için [Registration-Free COM birlikte çalışma](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Yönetilen kod ve veriler  
 Kod, .NET Framework olarak adlandırılır için geliştirilen *yönetilen kod*ve CLR tarafından kullanılan meta veriler içerir. .NET Framework uygulamaları tarafından kullanılan veri çağrılır *yönetilen verilerini* ayırma ve belleği geri kazanmak ve tür denetimi gibi verilerle ilgili görevler çalışma zamanı yönettiği için. Varsayılan olarak, Visual Basic .NET yönetilen kod ve veri kullanır ancak yönetilmeyen kod ve COM nesneleri (Bu sayfada daha sonra açıklanmıştır) birlikte çalışma derlemelerini kullanarak verileri erişebilirsiniz.  
  
## <a name="assemblies"></a>Bütünleştirilmiş kodlar  
 Bir derleme, bir .NET Framework uygulamasının birincil yapı taşıdır. Yerleşik, oluşturulan ve dağıtılan bir veya daha fazla dosya içeren bir tek uygulama birim olarak işlevleri koleksiyonudur. Her derleme, derleme bildirimi içerir.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Tür kitaplıkları ve derleme bildirimleri  
 Tür kitaplıkları, COM nesneleri, üye adları ve veri türleri gibi özellikleri açıklar. Derleme bildirimleri, .NET Framework uygulamaları için aynı işlevi gerçekleştirir. Bunlar aşağıdakiler hakkında bilgi içerir:  
  
- Derleme kimliği, sürüm, kültür ve dijital imza.  
  
- Derleme uygulamasını oluşturan dosyaları.  
  
- Türleri ve derlemeyi oluşturan kaynakları. Bu, ondan dışarı içerir.  
  
- Diğer derlemelerdeki derleme zamanı bağımlılıklarını.  
  
- Derlemenin düzgün çalışması gereken izinler.  
  
 Derlemeler ve derleme bildirimleri hakkında daha fazla bilgi için bkz. [.NET derlemeleri](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>İçeri ve dışarı aktarma tür kitaplıkları  
 Visual Studio, bir yardımcı programı, bilgileri bir .NET Framework uygulamasına bir tür kitaplığından içeri aktarmanıza olanak sağlar, Tlbimp içerir. Tlbexp yardımcı programını kullanarak derlemelerden tür kitaplıkları oluşturabilirsiniz.  
  
 Tlbimp ve Tlbexp hakkında daha fazla bilgi için bkz: [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md) ve [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri  
 Birlikte çalışma bütünleştirilmiş kodlarını arasında köprü yönetilen .NET Framework derlemelerine olan ve yönetilmeyen kod, COM Nesne üyeleri eşdeğeri .NET Framework eşleme üyeleri yönetilir. Birlikte çalışma derlemelerini Visual Basic .NET tarafından oluşturulan çoğu, birlikte çalışabilirlik hazırlama gibi COM nesneleri ile çalışma ayrıntılarını işler.  
  
## <a name="interoperability-marshaling"></a>Birlikte çalışabilirlik hazırlama  
 Tüm .NET Framework uygulamaları, nesnelerin kullanılan programlama diline bakılmaksızın birlikte çalışabilirliği sağlayan ortak türler bir kümesini paylaşır. Parametreler ve dönüş değerleri COM nesnelerinin bazen yönetilen kod içinde kullanılan farklı veri türleri kullanın. *Birlikte çalışabilirlik hazırlama* ve COM nesneleri dışarı taşırken paketleme parametreler ve dönüş değerleri eşdeğeri veri türlerini işlemidir. Daha fazla bilgi için [birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Birlikte Çalışma için Hazırlama](../../../framework/interop/interop-marshaling.md)
- [Kayıtsız COM Birlikte Çalışma](../../../framework/interop/registration-free-com-interop.md)
