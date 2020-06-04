---
title: Uygulama Web Hizmetlerine Erişme
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: cf9a0c9840b9228b59af9959cf3a4efb9a1d1ea0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410198"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="914a5-102">Uygulama Web Hizmetlerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="914a5-102">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="914a5-103">`My.WebServices`Nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="914a5-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="914a5-104">Her örnek isteğe bağlı olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="914a5-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="914a5-105">Bu Web hizmetlerine nesnenin özellikleri aracılığıyla erişebilirsiniz `My.WebServices` .</span><span class="sxs-lookup"><span data-stu-id="914a5-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="914a5-106">Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="914a5-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="914a5-107">Öğesinden devralan tüm sınıflar <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="914a5-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="914a5-108">Görevler</span><span class="sxs-lookup"><span data-stu-id="914a5-108">Tasks</span></span>

<span data-ttu-id="914a5-109">Aşağıdaki tabloda, bir uygulama tarafından başvurulan Web hizmetlerine erişmenin olası yolları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="914a5-109">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="914a5-110">Alıcı</span><span class="sxs-lookup"><span data-stu-id="914a5-110">To</span></span>|<span data-ttu-id="914a5-111">Bkz.</span><span class="sxs-lookup"><span data-stu-id="914a5-111">See</span></span>|
|---|---|
|<span data-ttu-id="914a5-112">Web hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="914a5-112">Call a Web service</span></span>|[<span data-ttu-id="914a5-113">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="914a5-113">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="914a5-114">Bir Web hizmetini zaman uyumsuz olarak çağırma ve tamamlandığında bir olayı işleme</span><span class="sxs-lookup"><span data-stu-id="914a5-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="914a5-115">Nasıl yapılır: Web Hizmetini Zaman Uyumsuz Çağırma</span><span class="sxs-lookup"><span data-stu-id="914a5-115">How to: Call a Web Service Asynchronously</span></span>](how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="914a5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="914a5-116">See also</span></span>

- [<span data-ttu-id="914a5-117">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="914a5-117">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
