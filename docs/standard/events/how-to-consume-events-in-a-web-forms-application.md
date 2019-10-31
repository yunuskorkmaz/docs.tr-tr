---
title: 'Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 1f95fd0dcc12f2d4e47ee07e1e6bb15d91000f0f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124780"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma
ASP.NET Web Forms uygulamalarında yaygın bir senaryo, bir Web sayfasını denetimlerle doldurmaktır ve sonra kullanıcının tıkladığı denetime göre belirli bir eylem gerçekleştirir. Örneğin, bir <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> denetimi kullanıcı Web sayfasında tıkladığı zaman bir olay oluşturur. Olayı işleyerek, uygulamanız ilgili düğme tıklayan için uygun uygulama mantığını gerçekleştirebilir.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Bir Web sayfasında düğme tıklatma olayını işlemek için  
  
1. Bir sonraki adımda tanımladığınız yöntemin adı olarak ayarlanmış `OnClick` değeri olan bir <xref:System.Web.UI.WebControls.Button> denetimine sahip bir ASP.NET Web Forms sayfası (Web sayfası) oluşturun.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <xref:System.Web.UI.WebControls.Button.Click> olay temsilcisi imzasıyla eşleşen ve `OnClick` değeri için tanımladığınız ada sahip bir olay işleyicisi tanımlayın.  
  
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
  
     <xref:System.Web.UI.WebControls.Button.Click> olayı, temsilci türü için <xref:System.EventHandler> sınıfını ve olay verileri için <xref:System.EventArgs> sınıfını kullanır. ASP.NET Page Framework, bir <xref:System.EventHandler> örneği oluşturan ve bu temsilci örneğini <xref:System.Web.UI.WebControls.Button> örneğinin <xref:System.Web.UI.WebControls.Button.Click> olayına ekleyen kodu otomatik olarak oluşturur.  
  
3. 2\. adımda tanımladığınız olay işleyicisi yönteminde, olay gerçekleştiğinde gerekli olan herhangi bir eylemi gerçekleştirmek için kod ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../docs/standard/events/index.md)
