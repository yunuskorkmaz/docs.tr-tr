---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: mevcut bir hizmet sözleşmesini kullanan bir iş akışı hizmeti oluşturma'
title: 'Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 0a31f0f4e205c72b857b59726437e896a7c68231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631261"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="ecccc-103">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecccc-103">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="ecccc-104">.NET Framework 4,5 özelliği, sözleşmenin ilk iş akışı geliştirme biçiminde Web Hizmetleri ve iş akışları arasında daha iyi tümleştirme sunar.</span><span class="sxs-lookup"><span data-stu-id="ecccc-104">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="ecccc-105">Sözleşme-ilk iş akışı geliştirme aracı, sözleşmeyi önce kod içinde tasarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecccc-105">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="ecccc-106">Araç daha sonra, sözleşmede bulunan işlemler için araç kutusunda bir etkinlik şablonu otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecccc-106">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecccc-107">Bu konuda, bir sözleşmenin ilk iş akışı hizmeti oluşturmaya yönelik adım adım yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecccc-107">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="ecccc-108">Sözleşme-ilk iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz. [Ilk Iş akışı hizmeti geliştirmeyi sözleşme](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="ecccc-108">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="ecccc-109">İş akışı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecccc-109">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="ecccc-110">Visual Studio'da, **Dosya**, **Yeni Proje**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-110">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="ecccc-111">**Şablonlar** ağacındaki **C#** düğümünün altında bulunan **WCF** düğümünü seçin ve **WCF iş akışı hizmeti uygulama** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-111">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="ecccc-112">Yeni projeyi adlandırın `ContractFirst` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-112">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="ecccc-113">Hizmet sözleşmesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecccc-113">Creating the service contract</span></span>  
  
1. <span data-ttu-id="ecccc-114">**Çözüm Gezgini** projeye sağ tıklayın ve **Ekle**, **Yeni öğe..**. seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-114">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="ecccc-115">Sol taraftaki **kod** düğümünü ve sağ taraftaki **sınıf** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-115">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="ecccc-116">Yeni sınıfı adlandırın `IBookService` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-116">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="ecccc-117">Görüntülenen kod penceresinin üst kısmında bir using ifadesi ekleyin `System.Servicemodel` .</span><span class="sxs-lookup"><span data-stu-id="ecccc-117">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="ecccc-118">Örnek sınıf tanımını aşağıdaki arabirim tanımına değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-118">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="ecccc-119">**CTRL + SHIFT + B** tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-119">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="ecccc-120">Hizmet sözleşmesini içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="ecccc-120">Importing the service contract</span></span>  
  
1. <span data-ttu-id="ecccc-121">**Çözüm Gezgini** ' de projeye sağ tıklayın ve **hizmet sözleşmesini içeri aktar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-121">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="ecccc-122">Altında **\<Current Project>** , tüm alt düğümleri açın ve **IBookService**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-122">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="ecccc-123">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-123">Click **OK**.</span></span>  
  
2. <span data-ttu-id="ecccc-124">Bir iletişim kutusu açılır, işlemin başarıyla tamamlandığını ve oluşturulan etkinliklerin, projeyi oluşturduktan sonra araç kutusu 'nda gözükgörünmediğini size uyaracaktır.</span><span class="sxs-lookup"><span data-stu-id="ecccc-124">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="ecccc-125">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-125">Click **OK**.</span></span>  
  
3. <span data-ttu-id="ecccc-126">İçeri aktarılan etkinliklerin araç kutusunda görünmesi için **CTRL + SHIFT + B** tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-126">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="ecccc-127">**Çözüm Gezgini**' de, Service1. xamlx ' yi açın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-127">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="ecccc-128">İş akışı hizmeti tasarımcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="ecccc-128">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="ecccc-129">**Sıra** etkinliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-129">Select the **Sequence** activity.</span></span> <span data-ttu-id="ecccc-130">Özellikler penceresi, **..** . öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-130">In the Properties window, click the **…**</span></span> <span data-ttu-id="ecccc-131">düğmesine basın. </span><span class="sxs-lookup"><span data-stu-id="ecccc-131">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="ecccc-132">Görüntülenen tür **koleksiyonu Düzenleyicisi** penceresinde, **tür** açılan listesine tıklayın ve **türlere gözatmayı seçin...**</span><span class="sxs-lookup"><span data-stu-id="ecccc-132">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="ecccc-133">girişte.</span><span class="sxs-lookup"><span data-stu-id="ecccc-133">entry.</span></span> <span data-ttu-id="ecccc-134">**Bir .NET türü görüntüle ve Seç** iletişim kutusunda, **\<Current Project>** tüm alt düğümler ' i açın ve **IBookService**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-134">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="ecccc-135">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-135">Click **OK**.</span></span> <span data-ttu-id="ecccc-136">**Tür koleksiyonu Düzenleyicisi** Iletişim kutusunda **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ecccc-136">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="ecccc-137">**ReceiveRequest** ve **SendResponse** etkinliklerini seçin ve silin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-137">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="ecccc-138">Araç kutusundan bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** etkinliğini **sıralı hizmet** etkinliğine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ecccc-138">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
