---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 907ad9a7dc3710a6e565de55c74a0d279d20e159
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765763"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="03d8d-103">Nasıl yapılır: veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="03d8d-103">How to: Add a data service reference (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="03d8d-104">WCF Veri Hizmetleri bir başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03d8d-104">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="03d8d-105">Bu, Visual Studio 'da geliştirdiğiniz bir istemci uygulamasındaki veri hizmetine daha kolay erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d8d-105">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="03d8d-106">Bu yordamı tamamladığınızda veri sınıfları, veri hizmetinden alınan meta veriler temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="03d8d-106">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="03d8d-107">Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="03d8d-107">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="03d8d-108">Veri hizmeti başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="03d8d-108">Add a data service reference</span></span>

1. <span data-ttu-id="03d8d-109">Seçim Veri hizmeti çözümün bir parçası değilse ve çalışır durumda değilse, veri hizmetini başlatın ve veri hizmetinin URI 'sini not edin.</span><span class="sxs-lookup"><span data-stu-id="03d8d-109">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="03d8d-110">Visual Studio 'da, **Çözüm Gezgini**, istemci projesine sağ tıklayın ve ardından   >  **hizmet başvurusu** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="03d8d-110">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="03d8d-111">Veri hizmeti geçerli çözümün parçasıysa **bul**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="03d8d-111">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="03d8d-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="03d8d-112">-or-</span></span>

     <span data-ttu-id="03d8d-113">**Adres** metin kutusuna veri hizmetinin temel URL 'sini yazın (gibi) `http://localhost:1234/Northwind.svc` ve ardından **Git**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="03d8d-113">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="03d8d-114">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="03d8d-114">Select **OK**.</span></span>

     <span data-ttu-id="03d8d-115">Veri hizmeti kaynaklarıyla erişebilen ve bunlarla etkileşime girebilen veri sınıflarını içeren yeni bir kod dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="03d8d-115">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="03d8d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03d8d-116">See also</span></span>

- [<span data-ttu-id="03d8d-117">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="03d8d-117">Quickstart</span></span>](quickstart-wcf-data-services.md)
