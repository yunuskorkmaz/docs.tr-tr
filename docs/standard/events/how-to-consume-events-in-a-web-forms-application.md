---
title: "Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma
Bir Web sayfası denetimleri ile doldurun ve ardından, kullanıcı Denetim göre belirli bir eylemi gerçekleştirmek için ASP.NET Web Forms uygulamalarında yaygın bir senaryo değil. Örneğin, bir <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> denetim isteğe bağlı olarak kullanıcı Web sayfasında, bir olay başlatır. Olay işleyerek uygulamanız için bu düğmeyi tıklatın uygun uygulama mantığını gerçekleştirebilirsiniz.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Bir Web sayfasında düğme tıklatma olayını işlemek için  
  
1.  Oluşturma sahip bir ASP.NET Web Forms sayfası (Web sayfası) bir <xref:System.Web.UI.WebControls.Button> ile kontrol `OnClick` değerine sonraki adımda tanımlayacaksınız yöntemin adı.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Eşleşen bir olay işleyicisi tanımlama <xref:System.Web.UI.WebControls.Button.Click> olay temsilci imza ve bu sahip için tanımlanmış adı `OnClick` değeri.  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <xref:System.Web.UI.WebControls.Button.Click> Olayı kullanan <xref:System.EventHandler> temsilci türü için sınıf ve <xref:System.EventArgs> olay verilerini sınıfı. ASP.NET sayfa çerçevesi örneği oluşturan kodu otomatik olarak oluşturur <xref:System.EventHandler> ve bu temsilci örneğine ekler <xref:System.Web.UI.WebControls.Button.Click> olayı <xref:System.Web.UI.WebControls.Button> örneği.  
  
3.  Olay, 2. adımda tanımladığınız işleyici yöntemi olay gerçekleştiğinde, gerekli olan herhangi bir eylem gerçekleştirmek için kod ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../docs/standard/events/index.md)
