---
title: Web Hizmetleri genel serileştirme teknolojisi örneği
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: b233ed4374231c7e7ff2b6617a63c4e4c94612c2
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46507878"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Web Hizmetleri genel serileştirme teknolojisi örneği
[Örneği indirin](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Bu örnek, ASP.NET Web Hizmetleri genel türler serileştirmek denetlemek ve nasıl kullanılacağını gösterir.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1.  Visual Studio açıp seçin **yeni Web sitesi** gelen **dosya** menüsü.  
  
2.  İçinde **yeni Web sitesi** iletişim kutusunda, sol bölmede, istediğiniz programlama dili seçin, sonra sağ bölmeden **ASP.NET Web hizmeti**.  
  
3.  Tıklayın **Gözat** ve \CS\GenericsService alt dizinine gidin.  
  
4.  Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.  
  
5.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
> [!NOTE]
>  Bu listedeki ilk beş adımları isteğe bağlıdır. .NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.  
  
> [!NOTE]
>  Örneği oluşturmak için aşağıdaki adımları gerekir.  
  
1.  Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve \CS alt dizinine gidin.  
  
2.  GenericsService alt simgesini sağ tıklatın ve seçin **paylaşım ve güvenlik**.  
  
3.  İçinde **Web Paylaşımı** sekmesinde **bu klasörü paylaş**.  
  
> [!IMPORTANT]
>  Listelenen sanal dizin adı Not **diğer adlar** bölmesinde örneği çalıştırmak için gerekeceği.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Internet Information Services kullanarak örneği oluşturmak için  
  
1.  Açık **Internet Information Services** yönetim ek bileşenini ve genişletme **Web siteleri**.  
  
2.  Sol tıklatma **varsayılan Web sitesi**seçin **yeni**ve ardından **sanal dizin?** oluşturmak için **sanal dizin oluşturma Sihirbazı**.  
  
3.  Tıklayın **sonraki**, sanal dizin için ortak diğer adı girin ve tıklayın **sonraki**.  
  
4.  Örnek (normal olarak \CS\GenericsService alt) kaydettiğiniz dizine yolu girin ve tıklayın **sonraki**. Tıklayın **sonraki** Sihirbazı tamamlamak için.  
  
> [!IMPORTANT]
>  Listelenen sanal dizin adı Not **diğer** bölmesinde örneği çalıştırmak için gerekeceği.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.  
  
2.  Tür `http://localhost/[virtual directory]/Service.asmx`burada `[virtual directory]` örnek yapılandırıldığında oluşturduğunuz sanal dizini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler. Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz. Daha fazla bilgi için [yapı XML Web hizmeti istemcileriyle](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>  
- <xref:System.Web.Services>  
- <xref:System.Xml.Serialization>  
- [Serileştirme](../../../docs/standard/serialization/index.md)  
- [ASP.NET ve XML Web hizmeti istemcileriyle kullanılarak oluşturulan XML Web Hizmetleri](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
