---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182761"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
Bu örnek, özel <xref:System.Activities.Presentation.View.ExpressionTextBox> bir etkinlik tasarımcısında nasıl kullanılacağını gösterir. Özel etkinlik, `MultiAssign`iki dize değişkenine iki dize değeri atar. Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimler <xref:System.Activities.InArgument>s'ye, bazıları <xref:System.Activities.OutArgument>da s'ye bağlanır.

## <a name="sample-details"></a>Örnek ayrıntılar
 İfadeleri `ArgumentToExpressionConverter` bağımsız değişkenlere bağlarken kullanılan tür dönüştürücüdür. Ayarlanmalıdır `ConverterParameter` `In` veya `Out` uygun olarak. `InOut`Desteklenmez.

 `OutArgument`Öznitelik, `UseLocationExpression` ifadenin Bir L değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için s üzerinde kullanılır. Çoğu durumda, L değeri ifadesi, `OutArgument` döndürülen değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcısıdır.

 Öznitelik `MaxLines` bu örnekte bir olarak `MinLines` ayarlanır ve ayarlanmaz. Bu, kullanıcı <xref:System.Activities.Presentation.View.ExpressionTextBox> tarafından yazılan metin miktarına bakılmaksızın bir satırın sabit boyutu olduğunu gösterir. Kullanıcı <xref:System.Activities.Presentation.View.ExpressionTextBox> girişine uyacak şekilde büyümesine `MaxLines` izin `MinLines`vermek için, 'den büyük.

 ExpressionTextBox yalnızca bağımsız değişkenlere bağlı olabilir ve CLR özelliklerine bağlanamaz.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010'u kullanarak ExpressionTextBoxSample.sln dosyasını açın.

2. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.

#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için

1. Çözüme yeni bir İş Akışı Konsolu Uygulaması ekleyin.

2. Yeni İş Akışı Konsolu Uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.

3. Çözümü derleyin.

4. **MultiAssign** etkinliğini araç kutusundan sürükleyin ve iş akışına bırakın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [İş Akışı Tasarımcısı ile Uygulama Geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
