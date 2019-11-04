---
title: 'Nasıl yapılır: Windows Formlarında Denetimleri Yeniden Boyutlandırma'
ms.date: 03/30/2017
f1_keywords:
- Size.Height
- Size.Width
helpviewer_keywords:
- controls [Windows Forms], resizing
- size [Windows Forms], controls
- Windows Forms controls, size
ms.assetid: d2dba441-a8c0-4705-b8e8-2e5d86d6e7ec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3aacc9434199eb7881e362a67e1fe0c08784c4a7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459547"
---
# <a name="how-to-resize-controls-on-windows-forms"></a><span data-ttu-id="d8a70-102">Nasıl yapılır: Windows Forms denetimleri yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="d8a70-102">How to: Resize controls on Windows Forms</span></span>

<span data-ttu-id="d8a70-103">Tek tek denetimleri yeniden boyutlandırabilir ve <xref:System.Windows.Forms.Button> ve <xref:System.Windows.Forms.GroupBox> denetimleri gibi aynı veya farklı türde birden çok denetimi yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8a70-103">You can resize individual controls, and you can resize multiple controls of the same or different kind, such as <xref:System.Windows.Forms.Button> and <xref:System.Windows.Forms.GroupBox> controls.</span></span>

## <a name="to-resize-a-control"></a><span data-ttu-id="d8a70-104">Bir denetimi yeniden boyutlandırmak için</span><span class="sxs-lookup"><span data-stu-id="d8a70-104">To resize a control</span></span>

<span data-ttu-id="d8a70-105">Visual Studio 'da yeniden boyutlandırılacak denetimi seçin ve sekiz boyutlandırma tutamaçlarından birini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d8a70-105">In Visual Studio, select the control to be resized and drag one of the eight sizing handles.</span></span>

> [!NOTE]
> <span data-ttu-id="d8a70-106">Denetimi seçin ve tek seferde bir piksel yeniden boyutlandırmak için **SHIFT** tuşunu basılı tutarken **ok** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d8a70-106">Select the control and press the **arrow** keys while holding down the **Shift** key to resize the control one pixel at a time.</span></span> <span data-ttu-id="d8a70-107">Denetimi büyük artışlarla yeniden boyutlandırmak için **SHIFT** ve **CTRL** tuşlarını basılı tutarken **aşağı oka** veya **sağ ok** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d8a70-107">Press the **down arrow** or **right arrow** keys while holding down the **Shift** and **Ctrl** keys to resize the control in large increments.</span></span>

## <a name="to-resize-multiple-controls-on-a-form"></a><span data-ttu-id="d8a70-108">Bir formdaki birden çok denetimi yeniden boyutlandırmak için</span><span class="sxs-lookup"><span data-stu-id="d8a70-108">To resize multiple controls on a form</span></span>

1. <span data-ttu-id="d8a70-109">Visual Studio 'da **CTRL** veya **SHIFT** tuşunu basılı tutarak yeniden boyutlandırmak istediğiniz denetimleri seçin.</span><span class="sxs-lookup"><span data-stu-id="d8a70-109">In Visual Studio, hold down the **Ctrl** or **Shift** key and select the controls you want to resize.</span></span> <span data-ttu-id="d8a70-110">Seçtiğiniz ilk denetimin boyutu diğer denetimler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8a70-110">The size of the first control you select is used for the other controls.</span></span>

2. <span data-ttu-id="d8a70-111">**Biçim** menüsünde, **aynı boyuta getir**' i seçin ve dört seçenekten birini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d8a70-111">On the **Format** menu, choose **Make Same Size**, and select one of the four options.</span></span> <span data-ttu-id="d8a70-112">İlk üç komut, denetimlerin boyutlarını, ilk seçilen denetimle eşleşecek şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d8a70-112">The first three commands change the dimensions of the controls to match the first-selected control.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8a70-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a70-113">See also</span></span>

- [<span data-ttu-id="d8a70-114">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="d8a70-114">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="d8a70-115">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="d8a70-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="d8a70-116">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="d8a70-116">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="d8a70-117">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="d8a70-117">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="d8a70-118">[Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms yeniden boyutlandırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8a70-118">[How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))</span></span>
