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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc1dee9377200e4c9fd575b8dcd00982db45f249
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317824"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="9e458-102">Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9e458-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="9e458-103">ASP.NET Web Forms uygulamalarında yaygın bir senaryo, bir Web sayfası denetimleri ile doldurun ve ardından, kullanıcı denetimi dayalı belirli bir eylemi gerçekleştirmek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9e458-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="9e458-104">Örneğin, bir <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> denetimi, kullanıcının Web sayfasında tıkladığında bir olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="9e458-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="9e458-105">Olayını işleyerek, uygulamanız için bu düğmeye tıklayın uygun uygulama mantığını gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e458-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="9e458-106">Bir Web sayfasında düğme tıklatma olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="9e458-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="9e458-107">Sahip bir ASP.NET Web Forms sayfası (Web sayfası) oluşturun bir <xref:System.Web.UI.WebControls.Button> denetimini `OnClick` değerine sonraki adımda tanımlayacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="9e458-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="9e458-108">Eşleşen bir olay işleyicisi tanımlama <xref:System.Web.UI.WebControls.Button.Click> olay temsilci imzası ve bu sahip için tanımlanan adını `OnClick` değeri.</span><span class="sxs-lookup"><span data-stu-id="9e458-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="9e458-109"><xref:System.Web.UI.WebControls.Button.Click> Olay kullanır <xref:System.EventHandler> temsilci türü için sınıf ve <xref:System.EventArgs> olay veri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9e458-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="9e458-110">ASP.NET sayfası framework örneği oluşturan kodu otomatik olarak oluşturduğu <xref:System.EventHandler> ve bu temsilci örneğine ekler <xref:System.Web.UI.WebControls.Button.Click> olayı <xref:System.Web.UI.WebControls.Button> örneği.</span><span class="sxs-lookup"><span data-stu-id="9e458-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="9e458-111">Olay işleyicisi yöntemi, 2. adımda tanımladığınız olay gerçekleştiğinde, gerekli olan herhangi bir eylem gerçekleştirmek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e458-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e458-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e458-112">See also</span></span>

- [<span data-ttu-id="9e458-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9e458-113">Events</span></span>](../../../docs/standard/events/index.md)
