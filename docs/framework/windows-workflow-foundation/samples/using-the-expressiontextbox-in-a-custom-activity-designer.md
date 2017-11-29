---
title: "Özel Etkinlik Tasarımcısı'nda ExpressionTextBox kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41a5d5645f66f69fd267b75359d0c74952b7b4bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Özel Etkinlik Tasarımcısı'nda ExpressionTextBox kullanma
Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Activities.Presentation.View.ExpressionTextBox> özel etkinlik Tasarımcısı'nda. Özel Etkinlik `MultiAssign`, iki dize değişkenleri iki dize değeri atar. Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimleri bağlamak için <xref:System.Activities.InArgument>s ve bazı bağlamak için <xref:System.Activities.OutArgument>s.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 `ArgumentToExpressionConverter` İfadeleri bağımsız değişkenleri bağlanırken kullanılan türü dönüştürücü. `ConverterParameter` Ayarlanmalıdır `In` veya `Out` uygun şekilde. `InOut`desteklenmiyor.  
  
 `UseLocationExpression` Özniteliği kullanılır `OutArgument`s ifade L-değeri ("sol value" veya "konum değeri") ifade gerektiğini belirtin. Çoğu durumda, L-değeri ifade belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcı olan `OutArgument` döndürülen bir değişken veya değişken adı değil.  
  
 `MaxLines` Özniteliği olarak ayarlanmış bir Bu örnekte ve `MinLines` ayarlı değil. Bu belirten <xref:System.Activities.Presentation.View.ExpressionTextBox> kullanıcı tarafından yazılan metin bakılmaksızın tek bir çizgi sabit bir boyuta sahiptir. İzin vermek için <xref:System.Activities.Presentation.View.ExpressionTextBox> kullanıcı girişi uyacak şekilde büyümesine olanak ayarlamak `MaxLines` büyük `MinLines`.  
  
 Bir ExpressionTextBox bağımsız değişken yalnızca bağlanabilir ve CLR özelliklerine bağlı olamaz.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ExpressionTextBoxSample.sln dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Yeni bir iş akışı konsol uygulaması çözüme ekleyin.  
  
2.  Bir başvuru ekleyin **ExpressionTextBoxSample** yeni bir iş akışı konsol uygulama projesi projeden.  
  
3.  Çözümü oluşturun.  
  
4.  Sürükleme **MultiAssign** araç etkinliğinden ve iş akışına bırakın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [İş Akışı Tasarımcısı ile uygulamaları geliştirme](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
