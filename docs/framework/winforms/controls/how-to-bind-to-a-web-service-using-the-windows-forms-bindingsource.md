---
title: 'Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 2f97a8c9b0d3f29ada108afaea92f39af3ac6b3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331006"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama
Windows Form denetimi bir XML Web hizmeti çağırma alınan sonuçları bağlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Windows.Forms.BindingSource> bileşeni. Bu yordam, bağlama için benzer bir <xref:System.Windows.Forms.BindingSource> bir türü için bileşen. Web hizmeti tarafından kullanıma sunulan türleri ve yöntemleri içeren bir istemci-tarafı proxy oluşturmanız gerekir. Bir istemci-tarafı proxy Web hizmeti (.asmx) kendisi ya da Web Hizmetleri Açıklama Dili (WSDL) dosyası oluşturur. Ayrıca, istemci tarafı proxy ortak özellik olarak Web hizmeti tarafından kullanılan karmaşık türler alanları açığa çıkarmalıdır. Ardından bağlama <xref:System.Windows.Forms.BindingSource> Web kullanıma sunulan türlerden proxy hizmeti.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Oluşturma ve bir istemci-tarafı proxy sunucuya bağlamak için  
  
1. Uygun bir ad alanı, seçtiğiniz dizine bir Windows formu oluşturun.  
  
2. Ekleme bir <xref:System.Windows.Forms.BindingSource> forma bileşen.  
  
3. Açık [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] komut istemi ve formunuza bulunan aynı dizine gidin.  
  
4. WSDL aracını kullanarak girin `wsdl` .asmx veya Web hizmeti için WSDL dosyasının URL'sini uygulamanızı ad alanı tarafından izlenen ve isteğe bağlı olarak dil çalışıyor.  
  
     Aşağıdaki kod örneği konumunda bulunan Web hizmetini kullanır `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`. Örneğin, C# türü için `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, veya Visual Basic türü `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Yolu için WSDL bağımsız değişken olarak geçirme aracı bir istemci-tarafı proxy aynı dizin ve ad alanı, uygulamanızda belirtilen dil olarak oluşturur. Visual Studio kullanıyorsanız, dosyayı projenize ekleyin.  
  
5. İstemci tarafı proxy bağlamak için bir tür seçin.  
  
     Web hizmeti tarafından sunulan bir yöntem tarafından döndürülen bir türü genellikle budur. Seçilen türündeki alanlar için bağlama amacıyla genel özellikleri olarak sunulmalıdır.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. Ayarlama <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource> istediğiniz diğer bir deyişle türe bulunan Web hizmeti taraflı proxy.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Bir Web hizmetine BindingSource denetimlerini bağlamak için  
  
-   Denetimlere bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource>, ortak özelliği, istediğiniz Web hizmet türü bir parametre olarak geçirerek.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.BindingSource> bir Web hizmeti bileşeni ve bir metin kutusunu bağlamak nasıl <xref:System.Windows.Forms.BindingSource> bileşeni. Düğmesine tıklayın, bir Web hizmeti yöntemi çağrılır ve sonuçları görünür `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu içeren tam bir örnek olduğundan bir `Main` yöntemi ve istemci tarafı proxy kodu kısaltılmış sürümü.  
  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing System.Web.Services, System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
