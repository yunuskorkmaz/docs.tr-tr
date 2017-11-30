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
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="d2eb2-102">Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2eb2-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="d2eb2-103">Bir Web sayfası denetimleri ile doldurun ve ardından, kullanıcı Denetim göre belirli bir eylemi gerçekleştirmek için ASP.NET Web Forms uygulamalarında yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="d2eb2-104">Örneğin, bir <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> denetim isteğe bağlı olarak kullanıcı Web sayfasında, bir olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="d2eb2-105">Olay işleyerek uygulamanız için bu düğmeyi tıklatın uygun uygulama mantığını gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="d2eb2-106">Bir Web sayfasında düğme tıklatma olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="d2eb2-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="d2eb2-107">Oluşturma sahip bir ASP.NET Web Forms sayfası (Web sayfası) bir <xref:System.Web.UI.WebControls.Button> ile kontrol `OnClick` değerine sonraki adımda tanımlayacaksınız yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="d2eb2-108">Eşleşen bir olay işleyicisi tanımlama <xref:System.Web.UI.WebControls.Button.Click> olay temsilci imza ve bu sahip için tanımlanmış adı `OnClick` değeri.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="d2eb2-109"><xref:System.Web.UI.WebControls.Button.Click> Olayı kullanan <xref:System.EventHandler> temsilci türü için sınıf ve <xref:System.EventArgs> olay verilerini sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="d2eb2-110">ASP.NET sayfa çerçevesi örneği oluşturan kodu otomatik olarak oluşturur <xref:System.EventHandler> ve bu temsilci örneğine ekler <xref:System.Web.UI.WebControls.Button.Click> olayı <xref:System.Web.UI.WebControls.Button> örneği.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="d2eb2-111">Olay, 2. adımda tanımladığınız işleyici yöntemi olay gerçekleştiğinde, gerekli olan herhangi bir eylem gerçekleştirmek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2eb2-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2eb2-112">See Also</span></span>  
 [<span data-ttu-id="d2eb2-113">Olayları</span><span class="sxs-lookup"><span data-stu-id="d2eb2-113">Events</span></span>](../../../docs/standard/events/index.md)
