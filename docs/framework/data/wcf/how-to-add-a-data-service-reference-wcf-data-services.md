---
title: 'Nasıl yapılır: Veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790745"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="950b3-102">Nasıl yapılır: Veri hizmeti başvurusu ekleme (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="950b3-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="950b3-103">WCF Veri Hizmetleri bir başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="950b3-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="950b3-104">Bu, Visual Studio 'da geliştirdiğiniz bir istemci uygulamasındaki veri hizmetine daha kolay erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="950b3-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="950b3-105">Bu yordamı tamamladığınızda veri sınıfları, veri hizmetinden alınan meta veriler temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="950b3-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="950b3-106">Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="950b3-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="950b3-107">Veri hizmeti başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="950b3-107">Add a data service reference</span></span>

1. <span data-ttu-id="950b3-108">Seçim Veri hizmeti çözümün bir parçası değilse ve çalışır durumda değilse, veri hizmetini başlatın ve veri hizmetinin URI 'sini not edin.</span><span class="sxs-lookup"><span data-stu-id="950b3-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="950b3-109">Visual Studio 'da, **Çözüm Gezgini**, istemci projesine sağ tıklayın ve ardından**hizmet başvurusu** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="950b3-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="950b3-110">Veri hizmeti geçerli çözümün parçasıysa **bul**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="950b3-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="950b3-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="950b3-111">-or-</span></span>

     <span data-ttu-id="950b3-112">**Adres** metin kutusuna veri hizmetinin temel URL 'sini yazın (gibi `http://localhost:1234/Northwind.svc`) ve ardından **Git**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="950b3-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="950b3-113">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="950b3-113">Select **OK**.</span></span>

     <span data-ttu-id="950b3-114">Veri hizmeti kaynaklarıyla erişebilen ve bunlarla etkileşime girebilen veri sınıflarını içeren yeni bir kod dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="950b3-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="950b3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="950b3-115">See also</span></span>

- [<span data-ttu-id="950b3-116">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="950b3-116">Quickstart</span></span>](quickstart-wcf-data-services.md)
