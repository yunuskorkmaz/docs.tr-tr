---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 7c1ba262046a665b8d63157fe3cdb4b1a41c37bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229387"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Presentation.View.ExpressionTextBox> özel etkinlik Tasarımcısı'nda. Özel Etkinlik `MultiAssign`, iki dize değişkenlerine iki dize değerleri atar. Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimlerini bağlamak için <xref:System.Activities.InArgument>s ve bazı bağlanma <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Örnek Ayrıntıları
 `ArgumentToExpressionConverter` Bağımsız değişken ifadeleri bağlanırken kullanılan türü dönüştürücü. `ConverterParameter` Ayarlanmalıdır `In` veya `Out` uygun şekilde. `InOut` desteklenmiyor.

 `UseLocationExpression` Özniteliği kullanılır `OutArgument`s ifade bir L-değeri ("sol value" veya "konum değeri") ifadesi olması gerektiğini belirtin. Çoğu durumda, bir L-değeri ifade göstermek için kullanılan geçerli bir Visual Basic tanımlayıcısı olan `OutArgument` iade edilmekte olan bir değişken veya değişken adı.

 `MaxLines` Özniteliği, bu örnekte birine ayarlanır ve `MinLines` ayarlı değil. Gösterir <xref:System.Activities.Presentation.View.ExpressionTextBox> tek satır metin kullanıcı tarafından yazılan bakılmaksızın sabit bir boyutu. İzin vermek için <xref:System.Activities.Presentation.View.ExpressionTextBox> kullanıcı girişi uyacak şekilde büyümesine olanak ayarlamak `MaxLines` büyüktür `MinLines`.

 Bir ExpressionTextBox bağımsız değişkenleri yalnızca bağlanabilir ve CLR özelliklerini bağlanamaz.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1.  Visual Studio 2010'u kullanarak, ExpressionTextBoxSample.sln dosyasını açın.

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için

1.  Çözüme yeni bir iş akışı konsol uygulaması ekleyin.

2.  Bir başvuru ekleyin **ExpressionTextBoxSample** proje yeni iş akışı konsol uygulaması projesi.

3.  Çözümü oluşturun.

4.  Sürükleme **MultiAssign** araç kutusundan ve iş akışına bırakın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [İş Akışı Tasarımcısı ile uygulama geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
