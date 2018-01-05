---
title: "Windows Forms Görsel Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 177b3034e9afc71a8ecc899364cc4911ef42a1a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="f126d-102">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="f126d-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="f126d-103">Bazen, bir proje için bir form önceki bir proje ile oluşturduğunuz bir benzer çağırır karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f126d-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="f126d-104">Ya da Filigran veya daha sonra yeniden bir projede özgün form şablonu değişiklikler içeren her bir yineleme ile kullanacağınız belirli denetim düzenini gibi ayarlarla temel form oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f126d-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="f126d-105">Form devralma, temel bir form oluşturun ve ardından ondan devralır ve ihtiyacınız ne olursa olsun özgün ayarlarına korurken değişiklik olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f126d-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="f126d-106">Türetilmiş sınıf forms program aracılığıyla veya görsel devralma Seçici kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f126d-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f126d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f126d-107">In This Section</span></span>  
 [<span data-ttu-id="f126d-108">Nasıl yapılır: Windows Forms’u Devralma</span><span class="sxs-lookup"><span data-stu-id="f126d-108">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 <span data-ttu-id="f126d-109">Devralınan formlar kod oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f126d-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="f126d-110">Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma</span><span class="sxs-lookup"><span data-stu-id="f126d-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="f126d-111">Devralınan formlar ile devralma Seçici oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f126d-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="f126d-112">Taban Formun Görünüşünü Değiştirmenin Etkileri</span><span class="sxs-lookup"><span data-stu-id="f126d-112">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="f126d-113">Taban formun denetimleri ve bunların özelliklerini değiştirmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f126d-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="f126d-114">İzlenecek Yol: Görsel Devralmayı Gösterme</span><span class="sxs-lookup"><span data-stu-id="f126d-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="f126d-115">Temel bir Windows formu oluşturma ve bir sınıf kitaplığı'na derlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="f126d-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="f126d-116">Bu sınıf kitaplığı başka bir projeye almak ve temel formundan devralan yeni bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f126d-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="f126d-117">Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f126d-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="f126d-118">Kullanma için yönergeler sağlar `GenerateMember` ve `Modifiers` Windows Form Tasarımcısı bileşeni için bir üye değişkenine oluşturduğunda, ilgili özellikler.</span><span class="sxs-lookup"><span data-stu-id="f126d-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f126d-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f126d-119">Related Sections</span></span>  
 [<span data-ttu-id="f126d-120">Devralma temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f126d-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="f126d-121">Diğer sınıflar için temel görevi gören Visual Basic sınıflarını tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="f126d-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="f126d-122">class</span><span class="sxs-lookup"><span data-stu-id="f126d-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="f126d-123">Tek devralma izin sınıfların C# yaklaşımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f126d-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="f126d-124">Devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="f126d-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="f126d-125">Olay işleyicileri devralınan bileşenleri ile ortaya ortak sorunları listeler</span><span class="sxs-lookup"><span data-stu-id="f126d-125">Lists common issues that arise with event handlers in inherited components</span></span>
