---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: dfb53096be59abd9924a024880d4125ca774d4b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267507"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma

Bu örnek, <xref:System.Activities.Presentation.View.ExpressionTextBox> bir özel etkinlik tasarımcısında ' nin nasıl kullanılacağını gösterir. Özel etkinlik, `MultiAssign` iki dize değişkenine iki dize değeri atar. Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> Denetimler s öğesine bağlanır <xref:System.Activities.InArgument> ve bazıları bazı <xref:System.Activities.OutArgument> öğeleri bağlar.

## <a name="sample-details"></a>Örnek Ayrıntılar

 `ArgumentToExpressionConverter`İfadeleri bağımsız değişkenlere bağlarken kullanılan tür dönüştürücüsü. `ConverterParameter`Ya da uygun şekilde ayarlanmalıdır `In` `Out` . `InOut` desteklenmez.

 `UseLocationExpression`Özniteliği, `OutArgument` Ifadesinin bir L-değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için kullanılır. Çoğu durumda, bir L-değer ifadesi, `OutArgument` döndürülmekte olan değişkenin bir değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcıdır.

 `MaxLines`Özniteliği bu örnekteki bir öğesine ayarlanır ve `MinLines` ayarlanmamış. Bu, <xref:System.Activities.Presentation.View.ExpressionTextBox> Kullanıcı tarafından yazılan metin miktarına bakılmaksızın bir satırın sabit bir boyutu olduğunu gösterir. <xref:System.Activities.Presentation.View.ExpressionTextBox>Kullanıcı girişine sığacak şekilde büyümeye izin vermek için, `MaxLines` büyüktür olarak ayarlayın `MinLines` .

 ExpressionTextBox yalnızca bağımsız değişkenlere bağlanabilir ve CLR özelliklerine bağlanamaz.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, ExpressionTextBoxSample. sln dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için

1. Çözüme yeni bir Iş akışı konsol uygulaması ekleyin.

2. Yeni Iş akışı konsol uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.

3. Çözümü derleyin.

4. Araç kutusundan **MultiAssign** etkinliğini sürükleyin ve iş akışına bırakın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
