---
title: Web Hizmetleri Genel Serileştirme Teknolojisi Örneği
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 467bfe1fd9eb8a0222385c34cb29a90df00dc937
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960759"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Web Hizmetleri Genel Serileştirme Teknolojisi Örneği
[Örnek indir](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Bu örnek, ASP.NET Web hizmetlerindeki genel türlerin serileştirilmesi ve denetimini nasıl kullanacağınızı gösterir.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1. Visual Studio 'Yu açın ve **Dosya** menüsünden **Yeni Web sitesi ' ni** seçin.  
  
2. **Yeni Web sitesi** iletişim kutusunda, istediğiniz programlama dilinizdeki sol bölmeden seçim yapın, ardından sağ bölmedeki **ASP.NET Web hizmeti**' ni seçin.  
  
3. **Göz at** ' a tıklayın ve \CS\GenericsService alt dizinine gidin.  
  
4. Visual Studio'da dosyayı açmak için QuoteService.asmx'e değiştirin seçin.  
  
5. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
> [!NOTE]
> Bu listedeki ilk beş adımları isteğe bağlıdır. .NET Framework çalışma zamanı, hizmet istenen Web hizmeti ilk zaman otomatik olarak oluşturur.  
  
> [!NOTE]
> Örneği oluşturmak için aşağıdaki adımları gerekir.  
  
1. Dosya Gezgini 'ni açın ve \CS alt dizinine gidin.  
  
2. GenericsService alt dizini simgesine sağ tıklayın ve **Paylaşım ve güvenlik**' i seçin.  
  
3. **Web Paylaşımı** sekmesinde **Bu klasörü paylaşma**' yı seçin.  
  
> [!IMPORTANT]
> **Diğer adlar** bölmesinde listelenen sanal dizin adını, örneği çalıştırmak için gerekli olacak şekilde bir yere göz atın.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Internet Information Services kullanarak örneği oluşturmak için  
  
1. **Internet Information Services** Yönetimi ek bileşenini açın ve **Web siteleri**' ni genişletin.  
  
2. **Varsayılan Web sitesi**' ni sağ tıklatın, **Yeni**' yi seçin ve ardından **sanal dizin?** ' i seçerek sanal **Dizin Oluşturma Sihirbazı**'nı oluşturun.  
  
3. **İleri**' ye tıklayın, sanal dizininizin ortak diğer adını girin ve **İleri**' ye tıklayın.  
  
4. Örneği kaydettiğiniz dizinin yolunu girin (normalde \CS\GenericsService alt dizini) ve **İleri**' ye tıklayın. **İleri** ' ye tıklayarak Sihirbazı sona erdirin.  
  
> [!IMPORTANT]
> **Diğer ad** bölmesinde listelenen sanal dizin adını, örneği çalıştırmak için gerekli olacak şekilde bir yere göz atın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.  
  
2. `http://localhost/[virtual directory]/Service.asmx` Türü`[virtual directory]` , örneği oluşturduğunuzda oluşturduğunuz sanal dizini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek Web hizmeti tanımının bağlantılar içeren bir varsayılan ASP.NET sayfasını görüntüler. Web hizmeti için kaynak kodu değiştirme ek olarak görünen özelleştirebilirsiniz. Daha fazla bilgi için bkz. [XML Web hizmeti Istemcileri oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Serileştirme](../../../docs/standard/serialization/index.md)
- [ASP.NET ve XML Web hizmeti Istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
