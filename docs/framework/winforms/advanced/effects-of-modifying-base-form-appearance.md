---
title: Taban Formun Görünüşünü Değiştirmenin Etkileri
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: b24bd2db564c7acb0a748c47095ee0777ea1eb88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955155"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="90431-102">Temel formun görünümünü değiştirmenin etkileri</span><span class="sxs-lookup"><span data-stu-id="90431-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="90431-103">Uygulama geliştirme sırasında, genellikle projedeki diğer formların (veya diğer projelerdeki) Devralındığı temel formun görünümünü değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="90431-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="90431-104">Tasarım zamanında, temel formun görünümünde yapılan değişiklikler (Özellikler ayarı veya denetimlerin eklenmesi ve çıkarılması), temel formu içeren proje yapılandırıldığında devralınan formlarda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="90431-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="90431-105">Değişiklikleri yalnızca temel formda kaydetmeniz yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="90431-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="90431-106">Bir proje oluşturmak için, **Yapı** menüsünden **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="90431-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="90431-107">Çalışma zamanında temel formda yapılan değişikliklerin önceden oluşturulan devralınmış formlarda hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="90431-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="90431-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90431-108">See also</span></span>

- [<span data-ttu-id="90431-109">base</span><span class="sxs-lookup"><span data-stu-id="90431-109">base</span></span>](../../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="90431-110">Nasıl yapılır: Windows Forms devralma</span><span class="sxs-lookup"><span data-stu-id="90431-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="90431-111">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="90431-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
