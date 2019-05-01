---
title: Windows Forms Görsel Devralma
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: e94cdc38b97f95cfe8a8504733298525c25667df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011872"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="52e7b-102">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="52e7b-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="52e7b-103">Bazen, bir proje için bir form benzer şekilde, önceki bir proje içinde oluşturduğunuz bir çağıran karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e7b-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="52e7b-104">Veya bir filigran ya da daha sonra yeniden içinde bir proje, özgün form şablonu değişiklikleri içeren her yineleme ile kullanacağınız belirli denetim düzeni gibi ayarları ile temel bir form oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e7b-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="52e7b-105">Form devralma, bir taban formunu oluşturmak ve ardından bu türden devralmalıdır ve değişiklik hangi özgün ayarlarına ihtiyacınız korurken sağlar.</span><span class="sxs-lookup"><span data-stu-id="52e7b-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="52e7b-106">Programlama yoluyla veya görsel devralma Seçici'yi kullanarak, türetilmiş sınıf formlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52e7b-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52e7b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="52e7b-107">In This Section</span></span>  
 [<span data-ttu-id="52e7b-108">Nasıl yapılır: Windows Form devralma</span><span class="sxs-lookup"><span data-stu-id="52e7b-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="52e7b-109">Devralınan form kod oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="52e7b-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="52e7b-110">Nasıl yapılır: Devralma Seçici iletişim kutusunu kullanarak form devralma</span><span class="sxs-lookup"><span data-stu-id="52e7b-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="52e7b-111">Devralınan form devralma Seçici ile oluşturma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="52e7b-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="52e7b-112">Taban Formun Görünüşünü Değiştirmenin Etkileri</span><span class="sxs-lookup"><span data-stu-id="52e7b-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="52e7b-113">Taban formun denetimler ve özellikleri değiştirmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="52e7b-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="52e7b-114">İzlenecek yol: Görsel devralmayı gösterme</span><span class="sxs-lookup"><span data-stu-id="52e7b-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="52e7b-115">Temel bir Windows formu oluşturun ve bir sınıf kitaplığı derleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="52e7b-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="52e7b-116">Bu sınıf kitaplığı, başka bir projeye içeri aktarmak ve temel formundan devralan yeni bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="52e7b-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="52e7b-117">Nasıl yapılır: Değiştiricileri ve GenerateMember özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="52e7b-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="52e7b-118">Kullanma için yönergeler sağlar `GenerateMember` ve `Modifiers` Windows Form Tasarımcısı ' bileşeni için bir üye değişkeni oluşturduğunda, ilgili özellikler.</span><span class="sxs-lookup"><span data-stu-id="52e7b-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52e7b-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="52e7b-119">Related Sections</span></span>  
 [<span data-ttu-id="52e7b-120">Devralma temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52e7b-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="52e7b-121">Diğer sınıflar için temel olarak hizmet veren bir Visual Basic sınıflarını tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="52e7b-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="52e7b-122">class</span><span class="sxs-lookup"><span data-stu-id="52e7b-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="52e7b-123">Açıklar C# yaklaşım sınıfların tek devralma verilir.</span><span class="sxs-lookup"><span data-stu-id="52e7b-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="52e7b-124">Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="52e7b-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="52e7b-125">Devralınan bileşenler olay işleyicileri ile ortaya çıkan ortak sorunları listeler</span><span class="sxs-lookup"><span data-stu-id="52e7b-125">Lists common issues that arise with event handlers in inherited components</span></span>
