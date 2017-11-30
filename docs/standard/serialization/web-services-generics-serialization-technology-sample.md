---
title: "Web Hizmetleri genel türler seri hale getirme teknolojisi örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b542149f211b037661bc662e7fc1f680aeb0e0ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="web-services-generics-serialization-technology-sample"></a>Web Hizmetleri genel türler seri hale getirme teknolojisi örneği
[Örnek indirme](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Bu örnek, kullanma ve ASP.NET Web Hizmetleri'nda genel türler serileştirmek denetim gösterilmektedir.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1.  Visual Studio'yu açın ve seçin **yeni Web sitesi** gelen **dosya** menüsü.  
  
2.  İçinde **yeni Web sitesi** iletişim kutusunda, sol bölmeden istediğiniz programlama dili seçin ve ardından sağ bölmeden **ASP.NET Web hizmeti**.  
  
3.  Tıklatın **Gözat** ve \CS\GenericsService alt dizinine gidin.  
  
4.  Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.  
  
5.  Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.  
  
> [!NOTE]
>  Bu listedeki ilk beş adımları isteğe bağlıdır. .NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.  
  
> [!NOTE]
>  Örneği oluşturmak için aşağıdaki adımları gerekir.  
  
1.  Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve \CS alt dizinine gidin.  
  
2.  GenericsService alt simgesine sağ tıklayın ve seçin **paylaşım ve güvenlik**.  
  
3.  İçinde **Web Paylaşımı** sekmesine **bu klasörü paylaş**.  
  
> [!IMPORTANT]
>  İçinde listelenen sanal dizin adını not edin **diğer adlar** bölmesinde, çünkü bu örneği çalıştırmak için gerekecektir.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Internet Information Services kullanarak örneği oluşturmak için  
  
1.  Açık **Internet Information Services** Yönetimi ek bileşenini ve genişletin **Web siteleri**.  
  
2.  Sol tıklatma **varsayılan Web sitesi**seçin **yeni**ve ardından **sanal dizin?** oluşturmak için **sanal dizin oluşturma Sihirbazı**.  
  
3.  Tıklatın **sonraki**, sanal dizin için ortak diğer adı girin ve tıklatın **sonraki**.  
  
4.  (Normalde \CS\GenericsService alt) örnek kaydettiğiniz dizinin yolunu girin ve tıklayın **sonraki**. Tıklatın **sonraki** Sihirbazı tamamlamak için.  
  
> [!IMPORTANT]
>  İçinde listelenen sanal dizin adını not edin **diğer ad** bölmesinde, çünkü örnek çalıştıracak şekilde gerekecektir.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.  
  
2.  Tür **http://localhost/ [sanal directory]/Service.asmx**, burada [sanal dizin] örneği oluşturulduğunda, oluşturduğunuz sanal dizini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler. Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz. Daha fazla bilgi için bkz: [XML Web hizmeti istemci derleme](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [Seri hale getirme](../../../docs/standard/serialization/index.md)  
 [ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)
