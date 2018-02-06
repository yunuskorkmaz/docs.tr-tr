---
title: "Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ebdd2d58f2fe502dbeb14148c303487774f531b
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2018
---
# <a name="interoperability-overview-c-programming-guide"></a>Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)
Konu C# yönetilen kodu ve yönetilmeyen kod birlikte çalışabilirliği sağlamak için yöntemleri açıklar.  
  
## <a name="platform-invoke"></a>Platform çağırma  
 *Platform Çağırma* etkinleştirir Microsoft Win32 API de gibi dinamik bağlantı kitaplıklarını (DLL'ler), uygulanan yönetilmeyen işlevleri çağırmak için kodu yönetilen bir hizmettir. Verilen işlevi çağırır bulur ve bağımsız değişkenleri (tamsayı, dize, diziler, yapıları ve benzeri) arasında birlikte çalışabilirlik sınır gerektiği şekilde sıralar.  
  
 Daha fazla bilgi için bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md) ve [nasıl yapılır: kullanım Wave dosyasını oynatmak için Platform Çağırma](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Ortak dil çalışma zamanı](../../../standard/clr.md) (CLR) sistem kaynaklarına erişimi yönetir. CLR dışında olan yönetilmeyen kodu çağırma bu güvenlik mekanizması atlar ve bu nedenle bir güvenlik riski oluşturur. Örneğin, yönetilmeyen kod doğrudan, yönetilmeyen kod CLR güvenlik mekanizmaları atlayarak kaynaklarında deniyor olabilir. Daha fazla bilgi için bkz: [.NET Framework Güvenliği](https://technet.microsoft.com/en-us/security/).  
  
## <a name="c-interop"></a>C++ Birlikte Çalışma  
 C++ birlikte çalışması, olarak da bilinen, yalnızca çalışır (IJW), böylece C# veya başka bir .NET Framework dil yazılan kod tarafından kullanılabilecek bir yerel C++ sınıfı kaydırmak için kullanabilirsiniz. Bunu yapmak için yerel bir DLL veya COM bileşeni sarmalamak için C++ kodunu yazın. Diğer .NET Framework dillerinin aksine [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] birlikte çalışabilirlik sağlar yönetilen ve yönetilmeyen aynı uygulama ve hatta aynı dosyada bulunması için kod desteği vardır. Ardından kullanarak C++ kodu derleme **/CLR** yönetilen bir derleme üretmek için derleyici anahtarı. Son olarak, C# projenize bir derlemesine başvuru ekleyin ve diğer yönetilen sınıflar kullanmak Sarmalanan nesneleri kullanır.  
  
## <a name="exposing-com-components-to-c"></a>C# COM bileşenlerini gösterme  
 Bir C# projesi bir COM bileşeni kullanabilir. Genel adımlar aşağıdaki gibidir:  
  
1.  Kullanın ve kaydetmek için bir COM bileşeni bulun. Regsvr32.exe kaydetmek veya kaydını – kayıt COM DLL kullanın.  
  
2.  Projeye COM bileşeni veya türü kitaplığına bir başvuru ekleyin.  
  
     Başvuru eklerken [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] kullanan [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), .NET Framework birlikte çalışma derlemesi çıktısını almak için giriş olarak bir tür kitaplığı alır. Ayrıca bir çalışma zamanı aranabilir sarmalayıcısı (RCW) adlı bir derlemeye yönetilen sınıflar ve COM sınıfları sarmalamak arabirimleri ve Tür Kitaplığı'nda bulunan arabirimlerin içerir. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]projeye oluşturulan derlemesine başvuru ekler.  
  
3.  RCW tanımlı bir sınıf örneği oluşturun. Bu, buna karşılık, COM nesnesinin örneği oluşturur.  
  
4.  Yalnızca diğer yönetilen nesneleri kullandıkça nesnesi kullanın. Nesne atık toplama tarafından iadesi, COM nesnesinin örneği bellekten de serbest bırakılır.  
  
 Daha fazla bilgi için bkz: [COM bileşenlerini .NET Framework'te gösterme](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>C# com'da gösterme  
 COM istemcileri doğru sunulan C# türleri kullanabilir. C# türleri kullanıma yönelik temel adımlar aşağıdaki gibidir:  
  
1.  Birlikte çalışma özniteliklerini C# projesinde ekleyin.  
  
     Bir derlemeyi COM değiştirerek görünür yapabileceğiniz [!INCLUDE[csprcs](~/includes/csprcs-md.md)] proje özellikleri. Daha fazla bilgi için bkz: [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Bir COM tür kitaplığı oluşturmak ve COM kullanımı için kaydolun.  
  
     Değiştirebileceğiniz [!INCLUDE[csprcs](~/includes/csprcs-md.md)] proje C# derleme COM birlikte çalışma için otomatik olarak kaydedilecek özellikleri. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]kullanan [Regasm.exe (derleme kayıt aracı)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)kullanarak `/tlb` komut satırı anahtarı, bir tür kitaplığı oluşturmak için yönetilen bir derleme giriş olarak alır. Bu tür kitaplığını açıklar `public` türleri derlemede ve COM istemcileri yönetilen sınıflar oluşturabilmesi için kayıt defteri girdileri ekler.  
  
 Daha fazla bilgi için bkz: [.NET Framework bileşenlerini COM'da gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) ve [örnek COM sınıfı](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birlikte çalışma performansını iyileştirme](https://msdn.microsoft.com/library/ms998551.aspx)  
 [COM ve .NET birlikte çalışabilirliği giriş](https://msdn.microsoft.com/library/office/bb610378.aspx)  
 [COM birlikte çalışma Visual Basic'te giriş](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 [Yönetilen ve yönetilmeyen kod arasında hazırlama](../../../../docs/framework/interop/interop-marshaling.md)  
 [Yönetilmeyen Kod ile Birlikte Çalışma](../../../../docs/framework/interop/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
