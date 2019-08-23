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
ms.openlocfilehash: 11a90615938da9e7dda5e05c55546918ccde137d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957096"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="4c934-102">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="4c934-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="4c934-103">Bazen, bir projenin önceki bir projede oluşturduğunuz bir form için çağrı yapmış olduğuna karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c934-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="4c934-104">Ya da, her bir yinelemeyle orijinal form şablonunda değişiklik içeren bir veya daha sonra bir proje içinde daha sonra kullanacağınız belirli denetim düzeni gibi ayarlarla temel bir form oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c934-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="4c934-105">Form devralma, bir temel form oluşturmanızı ve bundan sonra, ihtiyacınız olan özgün ayarları korurken değişiklik yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c934-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="4c934-106">Türetilmiş sınıf formları programlı bir şekilde veya görsel devralma seçiciyi kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c934-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c934-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4c934-107">In This Section</span></span>  
 [<span data-ttu-id="4c934-108">Nasıl yapılır: Windows Forms devralma</span><span class="sxs-lookup"><span data-stu-id="4c934-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="4c934-109">Kodda devralınan formlar oluşturmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c934-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="4c934-110">Nasıl yapılır: Devralma Seçici Iletişim kutusunu kullanarak formları devral</span><span class="sxs-lookup"><span data-stu-id="4c934-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="4c934-111">Devralma seçiciyle devralınan formlar oluşturmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c934-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="4c934-112">Taban Formun Görünüşünü Değiştirmenin Etkileri</span><span class="sxs-lookup"><span data-stu-id="4c934-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="4c934-113">Bir temel formun denetimlerini ve özelliklerini değiştirmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c934-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="4c934-114">İzlenecek yol: Görsel devralmayı gösterme</span><span class="sxs-lookup"><span data-stu-id="4c934-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="4c934-115">Temel bir Windows formu oluşturmayı ve bir sınıf kitaplığında derlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c934-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="4c934-116">Bu sınıf kitaplığını başka bir projeye içeri aktaracak ve temel formdan devralan yeni bir form oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4c934-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="4c934-117">Nasıl yapılır: Değiştiriciler ve GenerateMember özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="4c934-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="4c934-118">, Windows Form Tasarımcısı bir bileşen için `GenerateMember` üye `Modifiers` değişkeni oluşturduğunda ilgili ve özelliklerini kullanmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c934-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4c934-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4c934-119">Related Sections</span></span>  
 [<span data-ttu-id="4c934-120">Devralma Temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c934-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="4c934-121">Diğer sınıfların temeli olarak görev yapan Visual Basic sınıfların nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c934-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="4c934-122">class</span><span class="sxs-lookup"><span data-stu-id="4c934-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="4c934-123">Tek devralmaya izin verilen sınıfların C# yaklaşımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c934-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="4c934-124">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="4c934-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="4c934-125">Devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunları listeler</span><span class="sxs-lookup"><span data-stu-id="4c934-125">Lists common issues that arise with event handlers in inherited components</span></span>
