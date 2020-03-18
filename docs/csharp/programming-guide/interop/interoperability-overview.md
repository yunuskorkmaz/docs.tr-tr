---
title: Birlikte çalışabilirlik Genel Bakış - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 2c9eb2a8e6c2db8dc06ebe48ca6eb37d5cf638e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700737"
---
# <a name="interoperability-overview-c-programming-guide"></a>Birlikte Çalışabilirliğe Genel Bakış (C# Programlama Kılavuzu)
Konu, C# yönetilen kod ve yönetilmeyen kod arasında birlikte çalışabilirlik sağlamak için yöntemleri açıklar.  
  
## <a name="platform-invoke"></a>Platform Invoke  
 *Platform çağırma,* yönetilen kodun Microsoft Windows API'si gibi dinamik bağlantı kitaplıklarında (DLLs) uygulanan yönetilmeyen işlevleri çağırmasını sağlayan bir hizmettir. Dışa aktarılan bir işlevi bulur ve çağırır ve gerektiğinde interişlem sınırı boyunca bağımsız değişkenlerini (karşıtlar, dizeleri, diziler, yapılar vb.) sıralar.  
  
Daha fazla bilgi için, [Yönetilmeyen DLL Fonksiyonlarını Tüketme](../../../framework/interop/consuming-unmanaged-dll-functions.md) ve [WAV dosyasını oynatmak için platform çağırmanın nasıl kullanılacağı konusuna](./how-to-use-platform-invoke-to-play-a-wave-file.md)bakın.
  
> [!NOTE]
> [Ortak Dil Çalışma Süresi](../../../standard/clr.md) (CLR) sistem kaynaklarına erişimi yönetir. CLR dışında yönetilmeyen kod çağrı bu güvenlik mekanizması atlar ve bu nedenle bir güvenlik riski sunar. Örneğin, yönetilmeyen kod, CLR güvenlik mekanizmalarını atlayarak doğrudan yönetilmeyen koddaki kaynakları arayabilir. Daha fazla bilgi için [.NET'teki Güvenlik'e](../../../standard/security/index.md)bakın.  
  
## <a name="c-interop"></a>C++ Birlikte Çalışma  
 C# veya başka bir .NET Framework dilinde yazılmış kod tarafından tüketilebilmesi için yerel bir C++ sınıfına sarılbilmek için It Just Works (IJW) olarak da bilinen C++ interop'u kullanabilirsiniz. Bunu yapmak için, yerel bir DLL veya COM bileşenini sarmak için C++ kodu yazarsınız. Diğer .NET Framework dillerinden farklı olarak Visual C++, yönetilen ve yönetilmeyen kodun aynı uygulamada ve hatta aynı dosyada bulunmasını sağlayan birlikte çalışabilirlik desteğine sahiptir. Daha sonra yönetilen bir derleme oluşturmak için **/clr** derleyici anahtarını kullanarak C++ kodunu oluşturursunuz. Son olarak, C# projenizdeki derlemeye bir başvuru ekler ve diğer yönetilen sınıfları kullandığınız gibi sarılmış nesneleri kullanırsınız.  
  
## <a name="exposing-com-components-to-c"></a>COM Bileşenlerinin C'ye Teşhir Edilmesi\#
 Bir C# projesinden bir COM bileşeni ni tüketebilirsiniz. Genel adımlar şu şekildedir:  
  
1. Kullanmak ve kaydetmek için bir COM bileşeni bulun. Bir COM DLL'ye kaydolmak veya kaydını bırakmak için regsvr32.exe'yi kullanın.  
  
2. Projeye COM bileşenine veya tür kitaplığına bir başvuru ekleyin.  
  
     Başvuruyu eklediğinizde Visual Studio, bir .NET Framework interop derlemesini çıktılamak için bir tür kitaplığını girdi olarak alan [Tlbimp.exe 'yi (Tip Kitaplığı İçlemi)](../../../framework/tools/tlbimp-exe-type-library-importer.md)kullanır. Çalışma zamanı çağrılabilir sarıcı (RCW) olarak da adlandırılan derleme, com sınıflarını ve tür kitaplığındaki arabirimleri saran yönetilen sınıflar ve arabirimler içerir. Visual Studio projeye oluşturulan derlemeye bir başvuru ekler.  
  
3. RCW'de tanımlanan bir sınıfın örneğini oluşturun. Bu, sırayla, COM nesnesinin bir örneğini oluşturur.  
  
4. Nesneyi, yönetilen diğer nesneleri kullandığınız gibi kullanın. Nesne çöp toplama tarafından geri kazanıldığında, COM nesnesinin örneği de bellekten serbest bırakılır.  
  
 Daha fazla bilgi için [bkz.](../../../framework/interop/exposing-com-components.md)  
  
## <a name="exposing-c-to-com"></a>C#'nin COM'a teşhir edilmesi  
 COM istemcileri doğru şekilde maruz kalmış C# türlerini tüketebilir. C# türlerini ortaya çıkarmak için temel adımlar şunlardır:  
  
1. C# projesinde interop öznitelikleri ekleyin.  
  
     Visual C# proje özelliklerini değiştirerek derleme COM'u görünür hale getirebilirsiniz. Daha fazla bilgi için [Montaj Bilgileri İletişim Kutusu'na](/visualstudio/ide/reference/assembly-information-dialog-box)bakın.  
  
2. Com türü kitaplığı oluşturun ve COM kullanımına kaydedin.  
  
     Visual C# proje özelliklerini değiştirerek C# derlemesini COM interop'a otomatik olarak kaydedebilirsiniz. Visual Studio, bir tür kitaplığı oluşturmak için yönetilen `/tlb` bir derlemeyi girdi olarak alan komut satırı anahtarını kullanarak [Regasm.exe (Montaj Kayıt Aracı)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)kullanır. Bu tür kitaplık, derlemedeki `public` türleri açıklar ve COM istemcilerinin yönetilen sınıflar oluşturabilmesi için kayıt defteri girişleri ekler.  
  
 Daha fazla bilgi için [bkz.](../../../framework/interop/exposing-dotnet-components-to-com.md) [Example COM Class](./example-com-class.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Interop Performansını Artırma](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [COM ve .NET arasında birlikte çalışabilirlik giriş](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Visual Basic'te COM Interop'a Giriş](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Yönetilen ve Yönetilmeyen Kod arasında Marshaling](../../../framework/interop/interop-marshaling.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [C# Programlama Kılavuzu](../index.md)
