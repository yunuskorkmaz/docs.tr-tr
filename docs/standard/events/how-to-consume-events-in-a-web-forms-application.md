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
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="54a4a-102">Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma</span><span class="sxs-lookup"><span data-stu-id="54a4a-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="54a4a-103">web formları uygulamalarında ASP.NET yaygın bir senaryo, bir web sayfasını denetimlerle doldurmak ve ardından kullanıcının tıklatmalarını denetlediği belirli bir eylemi gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="54a4a-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="54a4a-104">Örneğin, kullanıcı <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> web sayfasında tıkladığında bir denetim bir olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="54a4a-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="54a4a-105">Olayı işleyerek, uygulamanız bu düğme tıklaması için uygun uygulama mantığını gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="54a4a-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="54a4a-106">Bir Web sayfasında düğme tıklatma olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="54a4a-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="54a4a-107">Bir sonraki adımda tanımladığınız yöntemin <xref:System.Web.UI.WebControls.Button> adına `OnClick` ayarlanan değerle denetimi olan bir ASP.NET Web Forms sayfası (web sayfası) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54a4a-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="54a4a-108">Olay temsilcisi imzasıyla <xref:System.Web.UI.WebControls.Button.Click> eşleşen ve değer için tanımladığınız adı `OnClick` içeren bir olay işleyicisi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="54a4a-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="54a4a-109">Olay, <xref:System.Web.UI.WebControls.Button.Click> temsilci <xref:System.EventHandler> türü için sınıfı <xref:System.EventArgs> ve olay verileri için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="54a4a-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="54a4a-110">ASP.NET sayfası çerçevesi otomatik olarak bir örnek oluşturan <xref:System.EventHandler> kod oluşturur ve <xref:System.Web.UI.WebControls.Button.Click> <xref:System.Web.UI.WebControls.Button> bu temsilci örneğini örnek olayına ekler.</span><span class="sxs-lookup"><span data-stu-id="54a4a-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="54a4a-111">Adım 2'de tanımladığınız olay işleyicisi yönteminde, olay oluştuğunda gerekli olan eylemleri gerçekleştirmek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54a4a-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a4a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54a4a-112">See also</span></span>

- [<span data-ttu-id="54a4a-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="54a4a-113">Events</span></span>](../../../docs/standard/events/index.md)
