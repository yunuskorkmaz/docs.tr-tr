---
title: "Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b24a367eaf78ef520cc2dd54db6ad58b215179ad
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-overview-c-programming-guide"></a>Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)
Konu C# yönetilen kodu ve yönetilmeyen kod birlikte çalışabilirliği sağlamak için yöntemleri açıklar.  
  
## <a name="platform-invoke"></a>Platform çağırma  
 *Platform Çağırma* etkinleştirir Microsoft Win32 API de gibi dinamik bağlantı kitaplıklarını (DLL'ler), uygulanan yönetilmeyen işlevleri çağırmak için kodu yönetilen bir hizmettir. Verilen işlevi çağırır bulur ve bağımsız değişkenleri (tamsayı, dize, diziler, yapıları ve benzeri) arasında birlikte çalışabilirlik sınır gerektiği şekilde sıralar.  
  
 Daha fazla bilgi için bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md) ve [nasıl yapılır: kullanım Wave dosyasını oynatmak için Platform Çağırma](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Ortak dil çalışma zamanı](../../../standard/clr.md) (CLR) sistem kaynaklarına erişimi yönetir. CLR dışında olan yönetilmeyen kodu çağırma bu güvenlik mekanizması atlar ve bu nedenle bir güvenlik riski oluşturur. Örneğin, yönetilmeyen kod doğrudan, yönetilmeyen kod CLR güvenlik mekanizmaları atlayarak kaynaklarında deniyor olabilir. Daha fazla bilgi için bkz: [.NET Framework Güvenliği](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="c-interop"></a>C++ Birlikte Çalışma  
 C++ birlikte çalışması, olarak da bilinen, yalnızca çalışır (IJW), böylece C# veya başka bir .NET Framework dil yazılan kod tarafından kullanılabilecek bir yerel C++ sınıfı kaydırmak için kullanabilirsiniz. Bunu yapmak için yerel bir DLL veya COM bileşeni sarmalamak için C++ kodunu yazın. Diğer .NET Framework dillerinin aksine [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] birlikte çalışabilirlik sağlar yönetilen ve yönetilmeyen aynı uygulama ve hatta aynı dosyada bulunması için kod desteği vardır. Ardından kullanarak C++ kodu derleme **/CLR** yönetilen bir derleme üretmek için derleyici anahtarı. Son olarak, C# projenize bir derlemesine başvuru ekleyin ve diğer yönetilen sınıflar kullanmak Sarmalanan nesneleri kullanır.  
  
## <a name="exposing-com-components-to-c"></a>C# COM bileşenlerini gösterme  
 Bir C# projesi bir COM bileşeni kullanabilir. Genel adımlar aşağıdaki gibidir:  
  
1.  Kullanın ve kaydetmek için bir COM bileşeni bulun. Regsvr32.exe kaydetmek veya kaydını – kayıt COM DLL kullanın.  
  
2.  Projeye COM bileşeni veya türü kitaplığına bir başvuru ekleyin.  
  
     Başvuru eklerken [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] kullanan [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382), .NET Framework birlikte çalışma derlemesi çıktısını almak için giriş olarak bir tür kitaplığı alır. Ayrıca bir çalışma zamanı aranabilir sarmalayıcısı (RCW) adlı bir derlemeye yönetilen sınıflar ve COM sınıfları sarmalamak arabirimleri ve Tür Kitaplığı'nda bulunan arabirimlerin içerir. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]projeye oluşturulan derlemesine başvuru ekler.  
  
3.  RCW tanımlı bir sınıf örneği oluşturun. Bu, buna karşılık, COM nesnesinin örneği oluşturur.  
  
4.  Yalnızca diğer yönetilen nesneleri kullandıkça nesnesi kullanın. Nesne atık toplama tarafından iadesi, COM nesnesinin örneği bellekten de serbest bırakılır.  
  
 Daha fazla bilgi için bkz: [COM bileşenlerini .NET Framework'te gösterme](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730).  
  
## <a name="exposing-c-to-com"></a>C# com'da gösterme  
 COM istemcileri doğru sunulan C# türleri kullanabilir. C# türleri kullanıma yönelik temel adımlar aşağıdaki gibidir:  
  
1.  Birlikte çalışma özniteliklerini C# projesinde ekleyin.  
  
     Bir derlemeyi COM değiştirerek görünür yapabileceğiniz [!INCLUDE[csprcs](~/includes/csprcs-md.md)] proje özellikleri. Daha fazla bilgi için bkz: [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Bir COM tür kitaplığı oluşturmak ve COM kullanımı için kaydolun.  
  
     Değiştirebileceğiniz [!INCLUDE[csprcs](~/includes/csprcs-md.md)] proje C# derleme COM birlikte çalışma için otomatik olarak kaydedilecek özellikleri. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]kullanan [Regasm.exe (derleme kayıt aracı)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)kullanarak `/tlb` komut satırı anahtarı, bir tür kitaplığı oluşturmak için yönetilen bir derleme giriş olarak alır. Bu tür kitaplığını açıklar `public` türleri derlemede ve COM istemcileri yönetilen sınıflar oluşturabilmesi için kayıt defteri girdileri ekler.  
  
 Daha fazla bilgi için bkz: [.NET Framework bileşenlerini COM'da gösterme](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) ve [örnek COM sınıfı](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birlikte çalışma performansını iyileştirme](http://go.microsoft.com/fwlink/?LinkId=99564)  
 [COM birlikte çalışma giriş](http://go.microsoft.com/fwlink/?LinkId=112406)  
 [Yönetilen ve yönetilmeyen kod arasında hazırlama](http://go.microsoft.com/fwlink/?LinkId=112398)  
 [Yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md)  
 [Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)
