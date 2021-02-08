---
description: "Hakkında daha fazla bilgi edinin: uygulama Web Hizmetleri 'Ne erişme (Visual Basic)"
title: Uygulama Web Hizmetlerine Erişme
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: 4efd35ed7c8f4251a749b85a45242af299a51e6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797893"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="e4d10-103">Uygulama Web Hizmetlerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4d10-103">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="e4d10-104">`My.WebServices`Nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4d10-104">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="e4d10-105">Her örnek isteğe bağlı olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e4d10-105">Each instance is instantiated on demand.</span></span> <span data-ttu-id="e4d10-106">Bu Web hizmetlerine nesnenin özellikleri aracılığıyla erişebilirsiniz `My.WebServices` .</span><span class="sxs-lookup"><span data-stu-id="e4d10-106">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="e4d10-107">Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e4d10-107">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="e4d10-108">Öğesinden devralan tüm sınıflar <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e4d10-108">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="e4d10-109">Görevler</span><span class="sxs-lookup"><span data-stu-id="e4d10-109">Tasks</span></span>

<span data-ttu-id="e4d10-110">Aşağıdaki tabloda, bir uygulama tarafından başvurulan Web hizmetlerine erişmenin olası yolları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e4d10-110">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="e4d10-111">Amaç</span><span class="sxs-lookup"><span data-stu-id="e4d10-111">To</span></span>|<span data-ttu-id="e4d10-112">Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4d10-112">See</span></span>|
|---|---|
|<span data-ttu-id="e4d10-113">Web hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="e4d10-113">Call a Web service</span></span>|[<span data-ttu-id="e4d10-114">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e4d10-114">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="e4d10-115">Bir Web hizmetini zaman uyumsuz olarak çağırma ve tamamlandığında bir olayı işleme</span><span class="sxs-lookup"><span data-stu-id="e4d10-115">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="e4d10-116">Nasıl yapılır: Web Hizmetini Zaman Uyumsuz Çağırma</span><span class="sxs-lookup"><span data-stu-id="e4d10-116">How to: Call a Web Service Asynchronously</span></span>](how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="e4d10-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4d10-117">See also</span></span>

- [<span data-ttu-id="e4d10-118">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e4d10-118">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
