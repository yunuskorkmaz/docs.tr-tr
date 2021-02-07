---
description: 'Daha fazla bilgi edinin: Iş akışı tasarım deneyimini özelleştirme'
title: İş Akışı Tasarım Deneyimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 02049f8b42de3de6e4dfdfe8a4151be1500bcca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742660"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="cd186-103">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cd186-103">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="cd186-104">Özel etkinlikler tasarlama ve Windows İş Akışı Tasarımcısı yeniden barındırma için senaryolar, .NET Framework 4 ' te büyük ölçüde basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd186-104">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="cd186-105">Geliştirme ve dağıtım artık daha kolay ve daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="cd186-105">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="cd186-106">Key altyapısal değişikliği, yeni etkinlik Tasarımcısı programlama modelinin Windows Presentation Foundation (WPF) üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="cd186-106">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="cd186-107">Bu sayede etkinlik tasarımcılarını bildirimli olarak tanımlayabilir ve diğer uygulamalardaki İş Akışı Tasarımcısı karşılaştırıcı kolay bir şekilde yeniden barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd186-107">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="cd186-108">Yeniden barındırma sırasında, IntelliSense veya Basitleştirilmiş bir ifade etki alanını desteklemek için özel bir ifade Düzenleyicisi geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cd186-108">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="cd186-109">Windows Communication Foundation (WCF) tümleştirmesi, iş akışı hizmetleri kullanımıyla daha sorunsuz hale geldi.</span><span class="sxs-lookup"><span data-stu-id="cd186-109">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="cd186-110">Özel etkinlik tasarımcıları ve model öğesi ağacı, yeniden barındırılan iş akışı tasarımcılarındaki tasarım zamanı deneyimlerini geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd186-110">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cd186-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cd186-111">In This Section</span></span>

 [<span data-ttu-id="cd186-112">Özel Etkinlik Tasarımcıları ve Şablonları Kullanma</span><span class="sxs-lookup"><span data-stu-id="cd186-112">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="cd186-113">Yeni özel etkinlik tasarımcıları ve şablonlarının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd186-113">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="cd186-114">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="cd186-114">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="cd186-115">Windows İş Akışı Tasarımcısı Visual Studio dışında nasıl yeniden barındırılacağını ve doğrulama hatalarının nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd186-115">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="cd186-116">Özel İfade Düzenleyicisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="cd186-116">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="cd186-117">Visual Studio 2010 dışında barındırılan iş akışı tasarımcıları ile kullanmak için özel bir ifade düzenleyicisinin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd186-117">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="cd186-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cd186-118">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="cd186-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd186-119">See also</span></span>

- [<span data-ttu-id="cd186-120">Windows Workflow Foundation’ı Genişletme</span><span class="sxs-lookup"><span data-stu-id="cd186-120">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="cd186-121">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="cd186-121">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="cd186-122">Özel Etkinlik Tasarımcıları</span><span class="sxs-lookup"><span data-stu-id="cd186-122">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="cd186-123">Tasarımcı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="cd186-123">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
