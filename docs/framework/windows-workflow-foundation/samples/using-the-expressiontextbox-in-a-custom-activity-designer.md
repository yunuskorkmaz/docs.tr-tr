---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6b581b42c882c12425a17b9a518f8957ca10898a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715544"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
Bu örnek, <xref:System.Activities.Presentation.View.ExpressionTextBox> özel bir etkinlik tasarımcısında nasıl kullanılacağını gösterir. `MultiAssign`özel etkinlik iki dize değişkenine iki dize değeri atar. Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimleri <xref:System.Activities.InArgument>s 'ye bağlanır ve bazı <xref:System.Activities.OutArgument>s öğesine bağlanır.

## <a name="sample-details"></a>Örnek Ayrıntılar
 `ArgumentToExpressionConverter`, ifadeleri bağımsız değişkenlere bağlarken kullanılan tür dönüştürücütür. `ConverterParameter` `In` veya `Out` uygun şekilde ayarlanmalıdır. `InOut` desteklenmez.

 `UseLocationExpression` özniteliği, ifadenin bir L-değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için `OutArgument`s üzerinde kullanılır. Çoğu durumda, bir L-değer ifadesi, döndürülmekte olan `OutArgument` bir değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcıdır.

 `MaxLines` özniteliği bu örnekte bir olarak ayarlanır ve `MinLines` ayarlı değildir. Bu, <xref:System.Activities.Presentation.View.ExpressionTextBox>, Kullanıcı tarafından yazılan metin miktarına bakılmaksızın, bir satırın sabit bir boyutu olduğunu gösterir. <xref:System.Activities.Presentation.View.ExpressionTextBox>, kullanıcı girişine sığacak şekilde büyümeye izin vermek için, `MinLines`daha büyük `MaxLines` ayarlayın.

 ExpressionTextBox yalnızca bağımsız değişkenlere bağlanabilir ve CLR özelliklerine bağlanamaz.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, ExpressionTextBoxSample. sln dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için

1. Çözüme yeni bir Iş akışı konsol uygulaması ekleyin.

2. Yeni Iş akışı konsol uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.

3. Çözümü oluşturun.

4. Araç kutusundan **MultiAssign** etkinliğini sürükleyin ve iş akışına bırakın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
