---
title: Web Hizmetleri Genel Serileştirme Teknolojisi Örneği
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 6549dc1c3d428a5fb74fe0212549ef3f3f6510d1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299663"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Web Hizmetleri Genel Serileştirme Teknolojisi Örneği
[Örneği indirin](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Bu örnek, ASP.NET Web Hizmetleri genel türler serileştirmek denetlemek ve nasıl kullanılacağını gösterir.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1. Visual Studio açıp seçin **yeni Web sitesi** gelen **dosya** menüsü.  
  
2. İçinde **yeni Web sitesi** iletişim kutusunda, sol bölmede, istediğiniz programlama dili seçin, sonra sağ bölmeden **ASP.NET Web hizmeti**.  
  
3. Tıklayın **Gözat** ve \CS\GenericsService alt dizinine gidin.  
  
4. Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.  
  
5. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
> [!NOTE]
>  Bu listedeki ilk beş adımları isteğe bağlıdır. .NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.  
  
> [!NOTE]
>  Örneği oluşturmak için aşağıdaki adımları gerekir.  
  
1. Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve \CS alt dizinine gidin.  
  
2. GenericsService alt simgesini sağ tıklatın ve seçin **paylaşım ve güvenlik**.  
  
3. İçinde **Web Paylaşımı** sekmesinde **bu klasörü paylaş**.  
  
> [!IMPORTANT]
>  Listelenen sanal dizin adı Not **diğer adlar** bölmesinde örneği çalıştırmak için gerekeceği.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Internet Information Services kullanarak örneği oluşturmak için  
  
1. Açık **Internet Information Services** yönetim ek bileşenini ve genişletme **Web siteleri**.  
  
2. Sol tıklatma **varsayılan Web sitesi**seçin **yeni**ve ardından **sanal dizin?** oluşturmak için **sanal dizin oluşturma Sihirbazı**.  
  
3. Tıklayın **sonraki**, sanal dizin için ortak diğer adı girin ve tıklayın **sonraki**.  
  
4. Örnek (normal olarak \CS\GenericsService alt) kaydettiğiniz dizine yolu girin ve tıklayın **sonraki**. Tıklayın **sonraki** Sihirbazı tamamlamak için.  
  
> [!IMPORTANT]
>  Listelenen sanal dizin adı Not **diğer** bölmesinde örneği çalıştırmak için gerekeceği.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.  
  
2. Tür `http://localhost/[virtual directory]/Service.asmx`burada `[virtual directory]` örnek yapılandırıldığında oluşturduğunuz sanal dizini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler. Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz. Daha fazla bilgi için [yapı XML Web hizmeti istemcileriyle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Serileştirme](../../../docs/standard/serialization/index.md)
- [ASP.NET ve XML Web hizmeti istemcileriyle kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
