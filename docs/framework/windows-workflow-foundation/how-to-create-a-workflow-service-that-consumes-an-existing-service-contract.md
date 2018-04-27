---
title: 'Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09c3f7656284dd73dd5f50c4ef9f77cd5adcbfe7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="9c88f-102">Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c88f-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="9c88f-103"> özellikleri daha iyi web hizmetleri ve iş akışları sözleşme ilk iş akışı geliştirme biçiminde arasında tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="9c88f-103"> features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="9c88f-104">Sözleşme ilk iş akışı geliştirme aracı kod sözleşmede ilk tasarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c88f-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="9c88f-105">Araç ardından otomatik olarak bir etkinlik şablonu sözleşmesindeki işlemleri için araç kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c88f-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c88f-106">Bu konu, bir sözleşme ilk iş akışı hizmeti oluşturma ile ilgili adım adım yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c88f-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9c88f-107"> önce anlaşma iş akışı hizmeti geliştirme bkz [sözleşme ilk iş akışı hizmeti geliştirme](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="9c88f-107"> contract-first workflow service development, see [Contract First Workflow Service Development](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="9c88f-108">İş akışı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c88f-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="9c88f-109">Visual Studio'da seçin **dosya**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="9c88f-110">Seçin **WCF** düğümü altında **C#** düğümünde **şablonları** ağacı ve seçin **WCF iş akışı hizmeti uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="9c88f-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="9c88f-111">Yeni proje adı `ContractFirst` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="9c88f-112">Hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c88f-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="9c88f-113">' Nde projeye sağ **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="9c88f-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="9c88f-114">Seçin **kod** sol düğümünde ve **sınıfı** sağdaki şablonu.</span><span class="sxs-lookup"><span data-stu-id="9c88f-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="9c88f-115">Yeni sınıf `IBookService` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="9c88f-116">Görüntülenen kodu penceresi üst kullanma deyimine `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="9c88f-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="9c88f-117">Örnek sınıf tanımını aşağıdaki arabirimi tanımını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9c88f-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  <span data-ttu-id="9c88f-118">Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="9c88f-119">Hizmet sözleşmesi içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="9c88f-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="9c88f-120">' Nde projeye sağ **Çözüm Gezgini** seçip **alma hizmet sözleşmesini**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="9c88f-121">Altında  **\<geçerli Proje >**, tüm alt düğümleri açıp seçin **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="9c88f-122">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9c88f-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="9c88f-123">Bu işlemi başarıyla tamamlandı ve Projeyi derledikten sonra görünecek oluşturulan etkinlikler Araç Kutusu'nda uyarı bir iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="9c88f-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="9c88f-124">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9c88f-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="9c88f-125">Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**, böylece içeri aktarılan etkinlikler araç kutusu'nda görünür.</span><span class="sxs-lookup"><span data-stu-id="9c88f-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="9c88f-126">İçinde **Çözüm Gezgini**, Service1.xamlx açın.</span><span class="sxs-lookup"><span data-stu-id="9c88f-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="9c88f-127">İş akışı hizmeti Tasarımcısı'nda görünür.</span><span class="sxs-lookup"><span data-stu-id="9c88f-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="9c88f-128">Seçin **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9c88f-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="9c88f-129">Özellikler penceresinde **...**</span><span class="sxs-lookup"><span data-stu-id="9c88f-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="9c88f-130">düğmesini **ImplementedContract** özelliği.</span><span class="sxs-lookup"><span data-stu-id="9c88f-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="9c88f-131">İçinde **türü Koleksiyonu Düzenleyicisi** görünen penceresini tıklatın **türü** açılan listesinde seçip **türleri için Gözat...**</span><span class="sxs-lookup"><span data-stu-id="9c88f-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="9c88f-132">girişi.</span><span class="sxs-lookup"><span data-stu-id="9c88f-132">entry.</span></span> <span data-ttu-id="9c88f-133">İçinde **göz atma ve seçme bir .net türü** iletişim altında  **\<geçerli Proje >**, tüm alt düğümleri açıp seçin **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="9c88f-134">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9c88f-134">Click **OK**.</span></span> <span data-ttu-id="9c88f-135">İçinde **türü Koleksiyonu Düzenleyicisi** iletişim kutusunda, tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9c88f-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="9c88f-136">Seçin ve delete **ReceiveRequest** ve **SendResponse** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="9c88f-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="9c88f-137">Araç Kutusu'ndan sürükleyin bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** etkinlik üzerine **sıralı hizmet** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9c88f-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
