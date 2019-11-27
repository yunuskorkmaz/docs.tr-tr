---
title: COM Birlikte Çalışma'ya Giriş
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: c7909b3b6a2c9f0b397b9621b7e5125c232be313
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353208"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Birlikte Çalışma'ya Giriş (Visual Basic)
Bileşen nesne modeli (COM), bir nesnenin işlevselliğini diğer bileşenlere sunma ve uygulamaları barındırmasına imkan tanır. COM nesneleri birçok yıl için Windows programlamasında temel alınırken, ortak dil çalışma zamanı (CLR) için tasarlanan uygulamalar birçok avantaj sunar.  
  
 .NET Framework uygulamalar, son olarak COM ile geliştirilen bu bunların yerini alır. Böylece, Visual Studio 'Yu kullanarak COM nesneleri kullanmanız veya oluşturmanız gerekebilir. COM veya *com*birlikte çalışabilirliğiyle birlikte çalışabilirlik, mevcut com nesnelerini kendi hızınızda .NET Framework geçiş yaparken kullanmanıza olanak sağlar.  
  
 COM bileşenleri oluşturmak için .NET Framework kullanarak kayıtsız COM birlikte çalışma kullanabilirsiniz. Bu, bir bilgisayara birden fazla sürüm yüklendiğinde hangi DLL sürümünün etkinleştirildiğini denetlemenize olanak tanır ve son kullanıcıların, bir bilgisayar üzerinde çalıştırılabileceği uygun bir dizine kopyalamak için XCOPY veya FTP kullanmasına izin verir. Daha fazla bilgi için bkz. [KAYıTSıZ com birlikte çalışma](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Yönetilen kod ve veriler  
 .NET Framework için geliştirilen kod, *yönetilen kod*olarak ADLANDıRıLıR ve CLR tarafından kullanılan meta verileri içerir. .NET Framework uygulamalar tarafından kullanılan verilere *yönetilen veriler* denir çünkü çalışma zamanı, bellek ayırma ve geri kazanma ve tür denetimi gerçekleştirme gibi verilerle ilgili görevleri yönetir. Varsayılan olarak, Visual Basic .NET yönetilen kod ve verileri kullanır, ancak birlikte çalışma derlemelerini (Bu sayfada daha sonra açıklanan) kullanarak COM nesnelerinin yönetilmeyen koduna ve verilerine erişebilirsiniz.  
  
## <a name="assemblies"></a>Derlemeler  
 Derleme, bir .NET Framework uygulamasının birincil yapı taşıdır. Oluşturulan, sürümlü ve bir veya daha fazla dosya içeren tek bir uygulama birimi olarak dağıtılan işlevlerin bir koleksiyonudur. Her derleme bir derleme bildirimi içerir.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Tür kitaplıkları ve derleme bildirimleri  
 Tür kitaplıkları, üye adları ve veri türleri gibi COM nesnelerinin özelliklerini tanımlıyor. Derleme bildirimleri .NET Framework uygulamalar için aynı işlevi gerçekleştirir. Bunlar aşağıdakiler hakkında bilgiler içerir:  
  
- Bütünleştirilmiş kod kimliği, sürüm, kültür ve dijital imza.  
  
- Derleme uygulamasını oluşturan dosyalar.  
  
- Derlemeyi oluşturan türler ve kaynaklar. Bu, içinden aktarılmış olanları içerir.  
  
- Diğer derlemelerde derleme zamanı bağımlılıkları.  
  
- Derlemenin doğru çalışması için gereken izinler.  
  
 Derlemeler ve derleme bildirimleri hakkında daha fazla bilgi için bkz. [.net 'Teki derlemeler](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Tür kitaplıklarını içeri ve dışarı aktarma  
 Visual Studio, bir tür kitaplığından .NET Framework uygulamasına bilgi aktarmanıza olanak tanıyan bir yardımcı program olan Tlbimp içerir. Tlbexp yardımcı programını kullanarak derlemelerden tür kitaplıkları oluşturabilirsiniz.  
  
 Tlbimp ve Tlbexp hakkında daha fazla bilgi için bkz. [Tlbimp. exe (tür kitaplığı Içeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md) ve [Tlbexp. exe (tür kitaplığı verme programı)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri  
 Birlikte çalışma derlemeleri yönetilen ve yönetilmeyen kod arasında köprü oluşturan .NET Framework, COM nesne üyelerini eşit .NET Framework yönetilen üyelere eşliyorlar. Visual Basic .NET tarafından oluşturulan birlikte çalışma derlemeleri, birlikte çalışabilirlik sıralaması gibi COM nesneleriyle çalışma hakkında pek çok ayrıntıyı idare edin.  
  
## <a name="interoperability-marshaling"></a>Birlikte çalışabilirlik sıralaması  
 Tüm .NET Framework uygulamalar, kullanılan programlama dilinden bağımsız olarak, nesnelerin birlikte çalışabilirliğini etkinleştiren ortak türler kümesini paylaşır. COM nesnelerinin parametreleri ve dönüş değerleri bazen yönetilen kodda kullanılanlardan farklı veri türlerini kullanır. *Birlikte çalışabilirlik sıralaması* , com nesnelerinden ve bunlara geçiş yaparken parametreleri paketleme ve eşdeğer veri türlerine döndürme işlemidir. Daha fazla bilgi için bkz. [birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md).  
  
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
