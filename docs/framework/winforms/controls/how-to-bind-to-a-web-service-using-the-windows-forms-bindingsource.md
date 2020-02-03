---
title: BindingSource kullanarak bir Web hizmetine bağlama
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
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746674"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama
Bir Windows form denetimini bir XML Web hizmeti çağırma işleminden elde edilen sonuçlara bağlamak istiyorsanız, bir <xref:System.Windows.Forms.BindingSource> bileşeni kullanabilirsiniz. Bu yordam <xref:System.Windows.Forms.BindingSource> bileşeni bir türe bağlamaya benzer. Web hizmeti tarafından sunulan yöntemleri ve türleri içeren bir istemci tarafı proxy oluşturmanız gerekir. Web hizmeti (. asmx) içinden veya Web Hizmetleri Açıklama Dili (WSDL) dosyasından bir istemci tarafı ara sunucu oluşturabilirsiniz. Ayrıca, istemci tarafı proxy 'niz Web hizmeti tarafından kullanılan karmaşık türlerin alanlarını genel özellikler olarak kullanıma sunmalıdır. Ardından <xref:System.Windows.Forms.BindingSource> Web hizmeti proxy 'sinde gösterilen türlerden birine bağlarsınız.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>İstemci tarafı ara sunucusu oluşturmak ve bu sunucuya bağlamak için  
  
1. Tercih ettiğiniz dizinde uygun bir ad alanı ile bir Windows formu oluşturun.  
  
2. Forma bir <xref:System.Windows.Forms.BindingSource> bileşeni ekleyin.  
  
3. Windows yazılım geliştirme seti (SDK) komut istemi ' ni açın ve formunuzun bulunduğu dizine gidin.  
  
4. WSDL aracını kullanarak Web hizmeti için. asmx veya WSDL dosyasının URL 'sini, ardından uygulamanızın ad alanını ve isteğe bağlı olarak çalıştığınız dili `wsdl` girin.  
  
     Aşağıdaki kod örneği `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`konumunda bulunan Web hizmetini kullanır. Örneğin, tür `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`C# için veya `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`Visual Basic türü için. Yolu WSDL aracına bir bağımsız değişken olarak geçirmek, uygulamanız ile aynı dizin ve ad alanında belirtilen dilde bir istemci tarafı ara sunucu oluşturur. Visual Studio kullanıyorsanız, dosyayı projenize ekleyin.  
  
5. Bağlanacak istemci tarafı proxy 'sinde bir tür seçin.  
  
     Bu genellikle Web hizmeti tarafından sunulan bir yöntem tarafından döndürülen türdür. Seçilen türdeki alanlar bağlama amaçları için ortak özellikler olarak kullanıma sunulmalıdır.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğini, Web hizmeti istemci tarafı proxy 'sinde yer alan istediğiniz türe ayarlayın.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Denetimleri bir Web hizmetine bağlı BindingSource 'a bağlamak için  
  
- Bir parametre olarak istediğiniz Web hizmeti türünün genel özelliğini geçirerek <xref:System.Windows.Forms.BindingSource>denetimleri bağlayın.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.BindingSource> bileşenini Web hizmetine bağlamayı ve sonra bir metin kutusunu <xref:System.Windows.Forms.BindingSource> bileşenine bağlamayı gösterir. Düğmeye tıkladığınızda, bir Web hizmeti yöntemi çağırılır ve sonuçlar `textbox1`görüntülenir.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu, bir `Main` yöntemi ve istemci tarafı proxy kodunun kısaltılmış bir sürümünü içeren tam bir örnektir.  
  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing, System. Web. Services, System. Windows. Forms ve System. xml derlemelerine başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
