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
ms.openlocfilehash: 3490b6fb89bfe6d7ac778078f58381bb5172e2fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288491"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma
ASP.NET Web Forms uygulamalarında yaygın bir senaryo, bir Web sayfasını denetimlerle doldurmaktır ve sonra kullanıcının tıkladığı denetime göre belirli bir eylem gerçekleştirir. Örneğin, bir <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> Denetim Kullanıcı Web sayfasında tıkladığı zaman bir olay oluşturur. Olayı işleyerek, uygulamanız ilgili düğme tıklayan için uygun uygulama mantığını gerçekleştirebilir.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Bir Web sayfasında düğme tıklatma olayını işlemek için  
  
1. Bir <xref:System.Web.UI.WebControls.Button> `OnClick` sonraki adımda tanımlayacaksınız yöntemin adı olarak ayarlanmış bir denetimi olan bir ASP.NET Web Forms sayfası (Web sayfası) oluşturun.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <xref:System.Web.UI.WebControls.Button.Click>Olay temsilcisi imzasıyla eşleşen ve değer için tanımladığınız ada sahip bir olay işleyicisi tanımlayın `OnClick` .  
  
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
  
     <xref:System.Web.UI.WebControls.Button.Click>Olay, <xref:System.EventHandler> temsilci türü için sınıfını ve <xref:System.EventArgs> Olay verileri için sınıfını kullanır. ASP.NET Page Framework bir örneği oluşturan kodu otomatik olarak oluşturur <xref:System.EventHandler> ve bu temsilci örneğini <xref:System.Web.UI.WebControls.Button.Click> Örneğin olayına ekler <xref:System.Web.UI.WebControls.Button> .  
  
3. 2. adımda tanımladığınız olay işleyicisi yönteminde, olay gerçekleştiğinde gerekli olan herhangi bir eylemi gerçekleştirmek için kod ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ekinlikler](index.md)
