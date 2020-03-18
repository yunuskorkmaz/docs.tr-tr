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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124780"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma
web formları uygulamalarında ASP.NET yaygın bir senaryo, bir web sayfasını denetimlerle doldurmak ve ardından kullanıcının tıklatmalarını denetlediği belirli bir eylemi gerçekleştirmektir. Örneğin, kullanıcı <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> web sayfasında tıkladığında bir denetim bir olayı yükseltir. Olayı işleyerek, uygulamanız bu düğme tıklaması için uygun uygulama mantığını gerçekleştirebilir.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Bir Web sayfasında düğme tıklatma olayını işlemek için  
  
1. Bir sonraki adımda tanımladığınız yöntemin <xref:System.Web.UI.WebControls.Button> adına `OnClick` ayarlanan değerle denetimi olan bir ASP.NET Web Forms sayfası (web sayfası) oluşturun.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. Olay temsilcisi imzasıyla <xref:System.Web.UI.WebControls.Button.Click> eşleşen ve değer için tanımladığınız adı `OnClick` içeren bir olay işleyicisi tanımlayın.  
  
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
  
     Olay, <xref:System.Web.UI.WebControls.Button.Click> temsilci <xref:System.EventHandler> türü için sınıfı <xref:System.EventArgs> ve olay verileri için sınıfı kullanır. ASP.NET sayfası çerçevesi otomatik olarak bir örnek oluşturan <xref:System.EventHandler> kod oluşturur ve <xref:System.Web.UI.WebControls.Button.Click> <xref:System.Web.UI.WebControls.Button> bu temsilci örneğini örnek olayına ekler.  
  
3. Adım 2'de tanımladığınız olay işleyicisi yönteminde, olay oluştuğunda gerekli olan eylemleri gerçekleştirmek için kod ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../docs/standard/events/index.md)
