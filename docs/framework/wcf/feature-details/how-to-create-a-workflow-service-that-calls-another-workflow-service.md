---
title: "Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0a3b9f77445e8629fb67d099c6d7944044897fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="85840-102">Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="85840-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>
<span data-ttu-id="85840-103">Başka bir iş akışı hizmetinden bilgi almak bir iş akışı hizmeti için bazen gereklidir.</span><span class="sxs-lookup"><span data-stu-id="85840-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span>  <span data-ttu-id="85840-104">Bu konuda, bir iş akışı hizmeti başka bir çağrı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85840-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="85840-105">Bu konuda, iki iş akışı hizmetleri oluşturacağız; bir giriş dizesi ilk hizmetin kullandığı dizesini ters kaydedildikten sonra büyük harfe dönüştürür giriş dizesi ve başka bir tersine çevirir bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="85840-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>  
  
### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="85840-106">Reverser iş akışı hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="85840-106">To create the Reverser workflow service</span></span>  
  
1.  <span data-ttu-id="85840-107">Çalıştırma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici olarak.</span><span class="sxs-lookup"><span data-stu-id="85840-107">Run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] as an administrator.</span></span>  
  
2.  <span data-ttu-id="85840-108">Seçin **dosya**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="85840-108">Select **File**, **New Project**.</span></span> <span data-ttu-id="85840-109">Altında **iş akışı** düğümünde **yüklü şablonlar** bölmesinde, **WCF iş akışı hizmeti uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="85840-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="85840-110">Çözüm adı `NestedServices` ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="85840-110">Name the solution `NestedServices` and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="85840-111">Altında **sunucuları**, olduğundan emin olun **kullanım yerel IIS Web sunucusu** seçilir.</span><span class="sxs-lookup"><span data-stu-id="85840-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="85840-112">Tıklatın **sanal dizini oluştur**.</span><span class="sxs-lookup"><span data-stu-id="85840-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="85840-113">Tıklatın **Tamam** sanal dizinin başarıyla oluşturulduğunu belirten iletişim kutusu içinde.</span><span class="sxs-lookup"><span data-stu-id="85840-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>  
  
4.  <span data-ttu-id="85840-114">Çözüm Gezgini'nde, yeniden adlandırmak için Service1.xamlx `StringReverserService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="85840-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>  
  
5.  <span data-ttu-id="85840-115">Üzerinde **proje özelliklerini** sayfasında yeni proje için **Web** sekmesi. Ayarlama **eylemi Başlat** için **belirli sayfa**, StringReverserService.xamlx başlatmak için sayfa olarak seçin.</span><span class="sxs-lookup"><span data-stu-id="85840-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>  
  
6.  <span data-ttu-id="85840-116">Tasarımcıda StringReverserService.xamlx açın ve varolan silin `ReceiveRequest` ve `SendReply` etkinlikleri ve ardından sürükleyin bir `ReceiveAndSendReply` mevcut dizisi etkinliğin etkinlik.</span><span class="sxs-lookup"><span data-stu-id="85840-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="85840-117">Ayarlama **OperationName** ReverseString için.</span><span class="sxs-lookup"><span data-stu-id="85840-117">Set the **OperationName** to ReverseString.</span></span>  
  
    2.  <span data-ttu-id="85840-118">Ayarlama **ServiceContractName** IReverseString için.</span><span class="sxs-lookup"><span data-stu-id="85840-118">Set the **ServiceContractName** to IReverseString.</span></span>  
  
    3.  <span data-ttu-id="85840-119">Seçin **CanCreateInstance** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="85840-119">Select the **CanCreateInstance** check box.</span></span>  
  
7.  <span data-ttu-id="85840-120">Seçin **SequentialService** etkinliği ve ardından **değişkenleri** Tasarımcısı'nın altındaki sekmesi.</span><span class="sxs-lookup"><span data-stu-id="85840-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="85840-121">StringToReverse ve dize türünde ReversedStringToReturn adlı iki yeni değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>  
  
8.  <span data-ttu-id="85840-122">Tıklatın **tanımla** bağlamak **alma** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="85840-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="85840-123">Tıklatın **parametreleri**ve StringToReverse için atar dize türünde InputString adlı bir parametre oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>  
  
9. <span data-ttu-id="85840-124">Tıklatın **tanımla** bağlamak **SendReplyToReceive** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="85840-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="85840-125">Tıklatın **parametreleri**ve ReversedStringToReturn için atanan dize türünde, ReversedString adlı bir parametre oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>  
  
10. <span data-ttu-id="85840-126">Hizmet mantığını uygulamak için StringLibrary adlı projeye yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="85840-127">Sınıf tanımını aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="85840-127">Replace the class definition with the following code.</span></span>  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. <span data-ttu-id="85840-128">Giriş, ReverseString yöntemini çağırmak için sürükleyin bir **InvokeMethod** araç etkinliğinden arasındaki boşluğu için **alma** ve **SendReply** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="85840-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="85840-129">Etkinlik özelliklerini aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="85840-129">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="85840-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="85840-130">**MethodName**: ReverseString</span></span>  
  
    2.  <span data-ttu-id="85840-131">**Sonuç**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="85840-131">**Result**: ReversedStringToReturn</span></span>  
  
    3.  <span data-ttu-id="85840-132">**Parametreleri**: ile yeni bir parametre oluşturmak bir **yönü** , giriş, bir **türü** , dizenin ve **değeri** StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="85840-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>  
  
    4.  <span data-ttu-id="85840-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="85840-133">**TargetType**: NestedServices.StringLibrary</span></span>  
  
12. <span data-ttu-id="85840-134">Hizmet, F5 tuşuna basarak sınayın.</span><span class="sxs-lookup"><span data-stu-id="85840-134">Test the service by pressing F5.</span></span> <span data-ttu-id="85840-135">WCF Test görünen istemcisinde ReverseString() yöntemini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="85840-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="85840-136">İstek bölmesinde girin `Sample` InputString parametresinin değeri için.</span><span class="sxs-lookup"><span data-stu-id="85840-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="85840-137">Tıklatın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="85840-137">Click **Invoke**.</span></span> <span data-ttu-id="85840-138">Hizmeti, "elpmaS" döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="85840-138">The service should return "elpmaS".</span></span>  
  
### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="85840-139">UpperCaser iş akışı hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="85840-139">To create the UpperCaser workflow service</span></span>  
  
1.  <span data-ttu-id="85840-140">NestedServices projesine sağ tıklatın ve **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="85840-140">Right-click the NestedServices project and select **Add**, **New Item**.</span></span> <span data-ttu-id="85840-141">İçinde **iş akışı** düğümü, select **WCF iş akışı hizmeti**ve yeni hizmet adı `UpperCaserService`.</span><span class="sxs-lookup"><span data-stu-id="85840-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="85840-142">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="85840-142">Click **Add**.</span></span> <span data-ttu-id="85840-143">Bu projeye UpperCaserService.xamlx adlı yeni bir iş akışı hizmeti eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85840-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>  
  
2.  <span data-ttu-id="85840-144">Tasarımcıda UpperCaserService.xamlx açın ve varolan silin **ReceiveRequest** ve `SendReply` etkinlikleri ve sürükleme bir `ReceiveAndSendReply` mevcut dizisi etkinliğin etkinlik.</span><span class="sxs-lookup"><span data-stu-id="85840-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="85840-145">Ayarlama **OperationName** UpperCaseString için.</span><span class="sxs-lookup"><span data-stu-id="85840-145">Set the **OperationName** to UpperCaseString.</span></span>  
  
    2.  <span data-ttu-id="85840-146">Ayarlama **ServiceContractName** IUpperCaseString için.</span><span class="sxs-lookup"><span data-stu-id="85840-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>  
  
    3.  <span data-ttu-id="85840-147">Seçin **CanCreateInstance** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="85840-147">Select the **CanCreateInstance** check box.</span></span>  
  
3.  <span data-ttu-id="85840-148">SequentialService etkinliği seçin ve ardından **değişkenleri** Tasarımcısı'nın altındaki sekmesi.</span><span class="sxs-lookup"><span data-stu-id="85840-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="85840-149">StringToUpper, StringToReverse ve dize türünde StringToReturn adlı üç yeni değişkenleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>  
  
4.  <span data-ttu-id="85840-150">Tıklatın **tanımla** bağlamak **alma** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="85840-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="85840-151">Tıklatın **parametreleri**ve StringToUpper için atar dize türünde InputString adlı bir parametre oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>  
  
5.  <span data-ttu-id="85840-152">Tıklatın **tanımla** bağlamak **SendReplyToReceive** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="85840-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="85840-153">Tıklatın **parametreleri**ve StringToReturn için atanan dize türünde, ModifiedString adlı bir parametre oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>  
  
6.  <span data-ttu-id="85840-154">Hizmet mantığını uygulamak için aşağıdaki kodu kullanarak StringLibrary sınıfında yeni bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  <span data-ttu-id="85840-155">Giriş, UpperCaseString yöntemini çağırmak için sürükleyin bir **InvokeMethod** araç etkinliğinden arasındaki boşluğu için **alma** ve **SendReply** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="85840-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="85840-156">Etkinlik özelliklerini aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="85840-156">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="85840-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="85840-157">**MethodName**: UpperCaseString</span></span>  
  
    2.  <span data-ttu-id="85840-158">**Sonuç**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="85840-158">**Result**: StringToReverse</span></span>  
  
    3.  <span data-ttu-id="85840-159">**Parametreleri**: ile yeni bir parametre oluşturmak bir **yönü** , giriş, bir **türü** , dizenin ve **değeri** StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="85840-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>  
  
    4.  <span data-ttu-id="85840-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="85840-160">**TargetType**: NestedServices.StringLibrary</span></span>  
  
8.  <span data-ttu-id="85840-161">Artık ilk hizmet üzerinde değiştirilmiş dizesini arayacağız.</span><span class="sxs-lookup"><span data-stu-id="85840-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="85840-162">Projeye sağ tıklayın ve seçin **hizmet Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="85840-162">Right-click the project and select **Add Service Reference**.</span></span> <span data-ttu-id="85840-163">Http://localhost/NestedServices/StringReverserService.xamlx hizmetine hizmet başvurusu ekleyin ve ilk Web hizmetine erişmek için özel bir etkinlik oluşturmak için projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85840-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>  
  
9. <span data-ttu-id="85840-164">Yeni Etkinlik örneği arasında iş akışı sürükleyin **InvokeMethod** etkinlik ve **SendReplyToReceive** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="85840-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="85840-165">Değişken StringToReverse yeni etkinliği ve değişken StringToReturn StringToReturn özelliğine InputString özelliğinin atayın.</span><span class="sxs-lookup"><span data-stu-id="85840-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>  
  
10. <span data-ttu-id="85840-166">NestedServices projesi için Özellikler sayfasını açın ve değiştirme **belirli sayfa** içinde **Web** UpperCaserService.xamlx sekmesine.</span><span class="sxs-lookup"><span data-stu-id="85840-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>  
  
11. <span data-ttu-id="85840-167">Hizmet, F5 tuşuna basarak sınayın.</span><span class="sxs-lookup"><span data-stu-id="85840-167">Test the service by pressing F5.</span></span> <span data-ttu-id="85840-168">WCF Test görünen istemcisinde ReverseString() yöntemini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="85840-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="85840-169">İstek bölmesinde girin `Sample` InputString parametresinin değeri için.</span><span class="sxs-lookup"><span data-stu-id="85840-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="85840-170">Tıklatın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="85840-170">Click **Invoke**.</span></span> <span data-ttu-id="85840-171">Hizmeti, "ELPMAS" döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="85840-171">The service should return "ELPMAS".</span></span>  
  
### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="85840-172">Hizmetleri çağırmak için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="85840-172">To create a client to call the services</span></span>  
  
1.  <span data-ttu-id="85840-173">İstemci çözümü olarak adlandırılan yeni bir konsol uygulama projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="85840-173">Add a new Console application project called Client to the solution.</span></span>  
  
2.  <span data-ttu-id="85840-174">İstemci projesine sağ tıklatın ve **hizmet Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="85840-174">Right-click the Client project and select **Add Service Reference**.</span></span> <span data-ttu-id="85840-175">Görüntülenen penceresinde **bulma**.</span><span class="sxs-lookup"><span data-stu-id="85840-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="85840-176">StringReverserService.xamlx seçin ve ad alanı olarak ReverseService girin.</span><span class="sxs-lookup"><span data-stu-id="85840-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="85840-177">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="85840-177">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="85840-178">Program.cs içinde Main yöntemini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="85840-178">Replace the Main method in Program.cs with the following code.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
