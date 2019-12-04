---
title: İş Akışı Tasarım Deneyimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 27be398d874747b65ae051224070d3f40f1fbbb0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715131"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="41538-102">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="41538-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="41538-103">Özel etkinlikler tasarlama ve Windows İş Akışı Tasarımcısı yeniden barındırma için senaryolar, .NET Framework 4 ' te büyük ölçüde basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41538-103">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="41538-104">Geliştirme ve dağıtım artık daha kolay ve daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="41538-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="41538-105">Key altyapısal değişikliği, yeni etkinlik Tasarımcısı programlama modelinin Windows Presentation Foundation (WPF) üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="41538-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="41538-106">Bu sayede etkinlik tasarımcılarını bildirimli olarak tanımlayabilir ve diğer uygulamalardaki İş Akışı Tasarımcısı karşılaştırıcı kolay bir şekilde yeniden barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41538-106">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="41538-107">Yeniden barındırma sırasında, IntelliSense veya Basitleştirilmiş bir ifade etki alanını desteklemek için özel bir ifade Düzenleyicisi geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="41538-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="41538-108">Windows Communication Foundation (WCF) tümleştirmesi, iş akışı hizmetleri kullanımıyla daha sorunsuz hale geldi.</span><span class="sxs-lookup"><span data-stu-id="41538-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="41538-109">Özel etkinlik tasarımcıları ve model öğesi ağacı, yeniden barındırılan iş akışı tasarımcılarındaki tasarım zamanı deneyimlerini geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41538-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="41538-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="41538-110">In This Section</span></span>

 [<span data-ttu-id="41538-111">Özel Etkinlik Tasarımcıları ve Şablonları Kullanma</span><span class="sxs-lookup"><span data-stu-id="41538-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="41538-112">Yeni özel etkinlik tasarımcıları ve şablonlarının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="41538-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="41538-113">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="41538-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="41538-114">Windows İş Akışı Tasarımcısı Visual Studio dışında nasıl yeniden barındırılacağını ve doğrulama hatalarının nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="41538-114">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="41538-115">Özel İfade Düzenleyicisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="41538-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="41538-116">Visual Studio 2010 dışında barındırılan iş akışı tasarımcıları ile kullanmak için özel bir ifade düzenleyicisinin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="41538-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="41538-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="41538-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="41538-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41538-118">See also</span></span>

- [<span data-ttu-id="41538-119">Windows Workflow Foundation’ı Genişletme</span><span class="sxs-lookup"><span data-stu-id="41538-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="41538-120">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="41538-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="41538-121">Özel Etkinlik Tasarımcıları</span><span class="sxs-lookup"><span data-stu-id="41538-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="41538-122">Tasarımcıyı Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="41538-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
