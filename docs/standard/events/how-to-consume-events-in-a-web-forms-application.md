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
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="ef68a-102">Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef68a-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="ef68a-103">ASP.NET Web Forms uygulamalarında yaygın bir senaryo, bir Web sayfasını denetimlerle doldurmaktır ve sonra kullanıcının tıkladığı denetime göre belirli bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ef68a-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="ef68a-104">Örneğin, bir <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> denetimi kullanıcı Web sayfasında tıkladığı zaman bir olay oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef68a-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="ef68a-105">Olayı işleyerek, uygulamanız ilgili düğme tıklayan için uygun uygulama mantığını gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ef68a-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="ef68a-106">Bir Web sayfasında düğme tıklatma olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="ef68a-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="ef68a-107">Bir sonraki adımda tanımladığınız yöntemin adı olarak ayarlanmış `OnClick` değeri olan bir <xref:System.Web.UI.WebControls.Button> denetimine sahip bir ASP.NET Web Forms sayfası (Web sayfası) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef68a-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="ef68a-108"><xref:System.Web.UI.WebControls.Button.Click> olay temsilcisi imzasıyla eşleşen ve `OnClick` değeri için tanımladığınız ada sahip bir olay işleyicisi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ef68a-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="ef68a-109"><xref:System.Web.UI.WebControls.Button.Click> olayı, temsilci türü için <xref:System.EventHandler> sınıfını ve olay verileri için <xref:System.EventArgs> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef68a-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="ef68a-110">ASP.NET Page Framework, bir <xref:System.EventHandler> örneği oluşturan ve bu temsilci örneğini <xref:System.Web.UI.WebControls.Button> örneğinin <xref:System.Web.UI.WebControls.Button.Click> olayına ekleyen kodu otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef68a-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="ef68a-111">2\. adımda tanımladığınız olay işleyicisi yönteminde, olay gerçekleştiğinde gerekli olan herhangi bir eylemi gerçekleştirmek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef68a-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef68a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef68a-112">See also</span></span>

- [<span data-ttu-id="ef68a-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ef68a-113">Events</span></span>](../../../docs/standard/events/index.md)
