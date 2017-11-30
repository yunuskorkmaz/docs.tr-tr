---
title: "COM Birlikte Çalışma'ya Giriş (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81a9d0fc7036ff1b821c46687541311f26113212
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Birlikte Çalışma'ya Giriş (Visual Basic)
Bileşen Nesne Modeli (COM) diğer bileşenler ve konak uygulamaların işlevselliğini kullanıma nesneyi sağlar. COM nesneleri Windows yıllardır programlama için temel olsa da, Ortak Dil Çalışma Zamanı Modülü (CLR) tasarlanmış uygulamaları birçok avantaj sunar.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]uygulamaları sonunda olanlar com ile geliştirilen değiştirir O zamana kadar kullanın veya kullanarak COM nesneleri oluşturmak yaptığınız [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]. COM birlikte çalışabilirliği veya *COM birlikte çalışma*, geçiş sırasında var olan COM nesneleri kullanmanıza olanak tanır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kendi hızınıza.  
  
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
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]bir yardımcı programı, bilgilerini tür kitaplığından içeri olanak sağlayan Tlbimp içeren bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama. Tlbexp yardımcı programını kullanarak derlemelerden tür kitaplıklarının oluşturabilir.  
  
 Tlbimp ve Tlbexp hakkında daha fazla bilgi için bkz: [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) ve [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri  
 Birlikte çalışma derlemeleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] köprüsü arasında yönetilen ve yönetilmeyen derlemeleri kod, eşleme COM Nesne üyeleri eşdeğerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yönetilen üyeler. Visual Basic .NET tarafından oluşturulan birlikte çalışma derlemeleri birçok birlikte çalışabilirlik hazırlama gibi COM nesneleri ile çalışma ayrıntılarını işler.  
  
## <a name="interoperability-marshaling"></a>Birlikte çalışabilirlik hazırlama  
 Tüm [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulamaları kullanılan programlama diline bakılmaksızın nesneleri birlikte çalışabilirliği sağlamak genel türleri kümesini paylaşır. Parametreler ve dönüş değerleri COM nesnelerinin bazen yönetilen kodda kullanılanlardan farklı veri türlerini kullanın. *Birlikte çalışabilirlik hazırlama* COM nesneleri gelen ve giden taşırken paketleme parametreler ve dönüş değerleri eşdeğer veri türlerine işlemidir. Daha fazla bilgi için bkz: [birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [İzlenecek yol: COM nesnelerinde kalıtım uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Yönetilmeyen kod ile birlikte çalışma](https://msdn.microsoft.com/library/sd10k43k)  
 [Birlikte çalışabilirlik sorunlarını giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md)  
 [Kayıtsız COM birlikte çalışma](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
