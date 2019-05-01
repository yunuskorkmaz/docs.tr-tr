---
title: 'Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: c2ca9c349718c3939d74d052ff0ed448879cd045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945580"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="b45cb-102">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="b45cb-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="b45cb-103">Özellikler, web hizmetleri ve iş akışları sözleşme öncelikli iş akışı geliştirme biçiminde arasındaki tümleştirme daha iyi.</span><span class="sxs-lookup"><span data-stu-id="b45cb-103">features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="b45cb-104">Sözleşme öncelikli iş akışı geliştirme aracı, kod sözleşmede ilk tasarlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b45cb-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="b45cb-105">Araç ardından otomatik olarak bir etkinlik şablonu sözleşme işlemleri için araç kutusunda oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b45cb-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b45cb-106">Bu konu, bir sözleşme öncelikli iş akışı hizmeti oluşturma ile ilgili adım adım yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b45cb-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="b45cb-107">Sözleşme öncelikli iş akışı hizmet geliştirme hakkında daha fazla bilgi için bkz: [sözleşme ilk iş akışı hizmet geliştirme](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="b45cb-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="b45cb-108">İş akışı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b45cb-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="b45cb-109">Visual Studio'da **dosya**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="b45cb-110">Seçin **WCF** düğümünde **C#** düğümünde **şablonları** ağaç ve seçin **WCF iş akışı hizmeti uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="b45cb-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="b45cb-111">Yeni proje adını `ContractFirst` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="b45cb-112">Hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b45cb-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="b45cb-113">Projeye sağ **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="b45cb-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="b45cb-114">Seçin **kod** solda, düğüm ve **sınıfı** sağdaki şablonu.</span><span class="sxs-lookup"><span data-stu-id="b45cb-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="b45cb-115">Yeni bir sınıf adı `IBookService` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="b45cb-116">Görünen kod penceresinde üst bir Using deyimi ekleyin `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="b45cb-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="b45cb-117">Örnek sınıf tanımına aşağıdaki arabirim tanımı için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b45cb-117">Change the sample class definition to the following interface definition.</span></span>  
  
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
  
4. <span data-ttu-id="b45cb-118">Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="b45cb-119">Hizmet sözleşmesi içe aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="b45cb-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="b45cb-120">Projeye sağ **Çözüm Gezgini** seçip **hizmet sözleşmesini içer aktar**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="b45cb-121">Altında  **\<geçerli Proje >**, tüm alt düğümleri açın ve seçin **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="b45cb-122">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b45cb-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="b45cb-123">Sizi, işlemi başarıyla tamamlandı ve Projeyi derledikten sonra görünecek oluşturulan etkinlikler araç kutusundan bir iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="b45cb-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="b45cb-124">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b45cb-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="b45cb-125">Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**, böylece içeri aktarılan etkinlikler araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="b45cb-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="b45cb-126">İçinde **Çözüm Gezgini**, Service1.xamlx açın.</span><span class="sxs-lookup"><span data-stu-id="b45cb-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="b45cb-127">İş akışı hizmetinin tasarımcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="b45cb-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="b45cb-128">Seçin **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b45cb-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="b45cb-129">Özellikler penceresinde tıklayın **...**</span><span class="sxs-lookup"><span data-stu-id="b45cb-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="b45cb-130">düğmesini **ImplementedContract** özelliği.</span><span class="sxs-lookup"><span data-stu-id="b45cb-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="b45cb-131">İçinde **Editor Typu Kolekce** penceresine tıklayın **türü** açılır listesinde seçip **vyhledat Typy...**</span><span class="sxs-lookup"><span data-stu-id="b45cb-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="b45cb-132">girişi.</span><span class="sxs-lookup"><span data-stu-id="b45cb-132">entry.</span></span> <span data-ttu-id="b45cb-133">İçinde **göz atın ve bir .NET türü seçin** iletişim altında  **\<geçerli Proje >**, tüm alt düğümleri açın ve seçin **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="b45cb-134">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b45cb-134">Click **OK**.</span></span> <span data-ttu-id="b45cb-135">İçinde **Editor Typu Kolekce** iletişim kutusunda, tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b45cb-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="b45cb-136">Seçip silin **ReceiveRequest** ve **SendResponse** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b45cb-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="b45cb-137">Araç kutusundan sürükleyin bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** üzerine etkinlik **sıralı hizmeti** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b45cb-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
