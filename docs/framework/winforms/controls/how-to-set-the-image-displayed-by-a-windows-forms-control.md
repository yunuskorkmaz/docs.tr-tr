---
title: 'Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama'
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: b1b1dbbb50c3b19cf8d8a7d7030d0bc168afb6a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666196"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="09bdc-102">Nasıl yapılır: Windows Forms denetimi tarafından gösterilecek resmi ayarlama</span><span class="sxs-lookup"><span data-stu-id="09bdc-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="09bdc-103">Birçok Windows Forms denetimi görüntü görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="09bdc-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="09bdc-104">Bu görüntüler, Kaydet komutunu gösteren bir düğmedeki disket simgesi gibi denetimin amacını açıklığa kavuşturacak simgeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="09bdc-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="09bdc-105">Alternatif olarak, simgeler istediğiniz görünümü ve davranışı denetlemek için arka plan görüntüleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="09bdc-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="09bdc-106">Programatik</span><span class="sxs-lookup"><span data-stu-id="09bdc-106">Programmatic</span></span>

<span data-ttu-id="09bdc-107">Denetimin `Image` veya `BackgroundImage` özelliğini türünde<xref:System.Drawing.Image>bir nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="09bdc-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="09bdc-108">Genellikle, <xref:System.Drawing.Image.FromFile%2A> yöntemini kullanarak görüntüyü bir dosyadan yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="09bdc-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="09bdc-109">Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol **Resimlerim** klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="09bdc-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="09bdc-110">Windows işletim sistemini çalıştıran bilgisayarların çoğu bu dizini içerir.</span><span class="sxs-lookup"><span data-stu-id="09bdc-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="09bdc-111">Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="09bdc-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="09bdc-112">Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.PictureBox> denetim eklenmiş bir formunuza sahip olmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="09bdc-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a><span data-ttu-id="09bdc-113">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="09bdc-113">Designer</span></span>

1. <span data-ttu-id="09bdc-114">Visual Studio 'nun **Özellikler** penceresinde, denetimin **görüntüsünü** veya **BackgroundImage** özelliğini seçin ve ardından Seç ' i göstermek için üç nokta (![Visual Studio](./media/visual-studio-ellipsis-button.png)'da üç nokta düğmesini) seçin  **Kaynak** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="09bdc-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="09bdc-115">Göstermek istediğiniz görüntüyü seçin.</span><span class="sxs-lookup"><span data-stu-id="09bdc-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="09bdc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09bdc-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
