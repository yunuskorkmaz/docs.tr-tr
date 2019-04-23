---
title: Birlikte çalışabilirliğe genel bakış - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: cfe3b413506aa1383bbdaa9a89ffe42e3724a4a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337558"
---
# <a name="interoperability-overview-c-programming-guide"></a>Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)
Konu C# yönetilen kod ve yönetimsiz kod arasındaki birlikte çalışabilirliği sağlamak için yöntemleri açıklar.  
  
## <a name="platform-invoke"></a>Platform çağırma  
 *Platform Çağırma* sağlar dinamik bağlantı kitaplıklarını (DLL'ler) olarak uygulanır, yönetilmeyen işlevleri çağırmak için kod bu Microsoft Windows API gibi yönetilen bir hizmettir. Dışarı aktarılan bir işlevi çağırır bulur ve bağımsız değişkenlerinden (tamsayı, dizeler, diziler, yapılar ve benzeri) gerektiği gibi birlikte çalışabilirlik sınırında sürekliliğe devreder.  
  
 Daha fazla bilgi için [yönetilmeyen DLL işlevlerini kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md) ve [nasıl yapılır: Wave dosyasını oynatmak için Platform çağırma kullanma](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Ortak dil çalışma zamanı](../../../standard/clr.md) (CLR) sistem kaynaklarına erişimi yönetir. Dışında CLR yönetilmeyen kod çağırmak bu güvenlik mekanizmasını atlar ve bu nedenle güvenlik riski oluşturur. Örneğin, yönetilmeyen kod yönetilmeyen kodda doğrudan CLR güvenlik mekanizmaları atlayarak kaynakları çağırabilirsiniz. Daha fazla bilgi için [.NET içinde güvenlik](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>C++ Birlikte Çalışma  
 C++ birlikte çalışması, olarak da bilinir, yalnızca çalışır (IJW), yerel bir C++ sınıfı C# veya başka bir .NET Framework dilde yazılan kod tarafından tüketilebilir böylece sarmalamak için kullanabilirsiniz. Bunu yapmak için yerel bir DLL veya COM bileşeni sarmalamak için C++ kod yazın. Diğer .NET Framework dillerinde aksine [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] birlikte çalışabilirlik sağlar yönetilen ve yönetilmeyen kod aynı uygulama ve hatta aynı dosyanın bulunduğu desteği vardır. Ardından kullanarak C++ kodu derleme **/CLR** yönetilen bir bütünleştirilmiş kod üretmek için derleyici anahtarı. Son olarak, C# projenize derlemesine bir başvuru ekleyin ve diğer yönetilen sınıfları kullanırken Sarmalanan nesneleri kullanın.  
  
## <a name="exposing-com-components-to-c"></a>C için COM bileşenlerini gösterme\#
 Bir C# projeden bir COM bileşeni kullanabilir. Genel adımlar aşağıdaki gibidir:  
  
1. Kullanın ve kaydetmek için bir COM bileşeni bulun. Kaydedilecek regsvr32.exe veya Geri Al – kaydı bir COM DLL kullanın.  
  
2. Projeye bir COM bileşeni ya da tür kitaplığını bir başvuru ekleyin.  
  
     Bir başvuru eklediğinizde, Visual Studio kullanan [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), çıkış bir .NET Framework birlikte çalışma derlemesi için giriş olarak bir tür kitaplığı alır. Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) olarak da adlandırılan, derleme, yönetilen sınıflar ve arabirimler COM sınıfları sarmalamak ve tür kitaplığında bulunan arabirimlerin içerir. Visual Studio projesi için oluşturulan derlemeye bir başvuru ekler.  
  
3. RCW içinde tanımlanan bir sınıfın bir örneğini oluşturun. Bu, buna karşılık, COM nesnesinin örneği oluşturur.  
  
4. Yalnızca diğer yönetilen nesneleri kullanırken nesnesini kullanın. Nesne tarafından çöp toplama geri kazanılır, COM nesnesinin örneği de bellek serbest bırakılır.  
  
 Daha fazla bilgi için [COM bileşenlerini .NET Framework'te gösterme](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>C# com'da gösterme  
 COM istemcilerine doğru şekilde sunulan C# türleri kullanabilir. C# türleri kullanıma sunmak için temel adımlar aşağıdaki gibidir:  
  
1. C# projesinde birlikte çalışma özniteliklerini ekleyin.  
  
     Visual C# proje özelliklerini değiştirerek bir derlemenin COM görünür yapabilirsiniz. Daha fazla bilgi için [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Bir COM tür kitaplığı üretmek ve COM kullanım için kaydedin.  
  
     C# derleme COM birlikte çalışma için otomatik olarak kaydetmek için Visual C# proje özelliklerini değiştirebilirsiniz. Visual Studio kullanan [Regasm.exe (derleme kayıt aracı)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)kullanarak `/tlb` komut satırı anahtarı, bir tür kitaplığı oluşturmak için yönetilen bir derleme, girdi olarak alır. Bu tür kitaplığını açıklar `public` türleri derlemesinde ve kayıt defteri girdilerini ekler; böylece COM istemcileri yönetilen sınıfları oluşturabilirsiniz.  
  
 Daha fazla bilgi için [.NET Framework bileşenlerini COM'da gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) ve [örnek COM sınıfı](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Birlikte çalışma performansı iyileştirme](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [COM ve .NET arasında birlikte çalışabilirlik giriş](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Visual Basic'teki COM birlikte çalışma'ya giriş](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Yönetilen ve yönetilmeyen kod sıralama](../../../../docs/framework/interop/interop-marshaling.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../../docs/framework/interop/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
