---
title: "Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5024ad9000811aa438183de240c91b659644a7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama
XML Web hizmeti çağırma sonucu elde edilen sonuçlar Windows Form denetimi bağlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Windows.Forms.BindingSource> bileşeni. Bu yordam bağlama benzer bir <xref:System.Windows.Forms.BindingSource> türü için bileşen. Web hizmeti tarafından sunulan türleri ve yöntemleri içeren bir istemci-tarafı proxy oluşturmanız gerekir. Bir istemci-tarafı proxy Web hizmetinden (.asmx) kendisi ya da Web Hizmetleri Açıklama Dili (WSDL) dosyası oluşturun. Ayrıca, istemci-tarafı proxy, ortak özellik olarak Web hizmeti tarafından kullanılan karmaşık türler alanları açığa gerekir. Ardından bağlamak <xref:System.Windows.Forms.BindingSource> Web üzerinde açığa türlerinden birini proxy hizmet.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Oluşturma ve bir istemci-tarafı proxy bağlamak için  
  
1.  Uygun bir ad alanı ile tercih ettiğiniz dizininde bir Windows Form oluşturun.  
  
2.  Ekleme bir <xref:System.Windows.Forms.BindingSource> forma bileşen.  
  
3.  Açık [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] komut istemi ve formunuza bulunan aynı dizinine gidin.  
  
4.  WSDL aracını kullanarak girin `wsdl` .asmx veya WSDL dosyası Web hizmeti URL'sini ve ardından uygulamanızı ad alanı tarafından ve isteğe bağlı olarak dil çalıştığınız.  
  
     Aşağıdaki kod örneğinde http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx bulunan Web hizmetini kullanır. Örneğin, C# türü `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, veya Visual Basic türü `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Yolun WSDL için bağımsız değişken olarak geçirme aracı bir istemci-tarafı proxy aynı dizin ve ad alanı, uygulamanızda belirtilen dil olarak oluşturur. Kullanıyorsanız [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], dosyayı projenize ekleyin.  
  
5.  Bağlamak için istemci tarafı proxy bir tür seçin.  
  
     Bu genellikle Web hizmeti tarafından önerilen bir yöntem tarafından döndürülen bir türü olur. Seçilen türünde alanlar bağlama amacıyla için genel özellikleri olarak sunulmalıdır.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  Ayarlama <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource> istediğiniz diğer bir deyişle türünü bulunan Web hizmeti istemci-tarafı proxy'si.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Bir Web hizmetine bağlı BindingSource denetimleri bağlamak için  
  
-   Denetimlere bağlama <xref:System.Windows.Forms.BindingSource>, istediğiniz Web Hizmet türüne ilişkin ortak özelliği parametre olarak geçirme.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.BindingSource> bir Web hizmeti bileşeni ve bir metin kutusunu bağlamak nasıl <xref:System.Windows.Forms.BindingSource> bileşeni. Düğmesini tıklatın, bir Web hizmeti yöntemi olarak adlandırılır ve sonuçları görünür `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu içeren, tam bir örnektir bir `Main` yöntemi ve istemci tarafı proxy kodu kısaltılmış bir sürümü.  
  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing, System.Web.Services, System.Windows.Forms ve System.Xml derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [BindingSource bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Windows Forms denetimini bir türe bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
