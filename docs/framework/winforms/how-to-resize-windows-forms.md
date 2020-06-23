---
title: Formu yeniden boyutlandır
description: Boyut özelliği için yeni bir değer ayarlayarak formun yüksekliğini ve genişliğini yeniden boyutlandırmayı, ya da yükseklik veya genişlik özelliklerini ayrı ayrı ayarlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 0d6383e4d29d9407d3da97bf8b94761f06d99748
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903278"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="01204-103">Nasıl yapılır: Windows Forms’u Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="01204-103">How to: Resize Windows Forms</span></span>

<span data-ttu-id="01204-104">Windows formunuzun boyutunu birkaç şekilde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01204-104">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="01204-105">Özelliği için yeni bir değer ayarlayarak <xref:System.Windows.Forms.Form.Size%2A> ya da <xref:System.Windows.Forms.Control.Height%2A> veya <xref:System.Windows.Forms.Control.Width%2A> özelliklerini ayrı ayrı ayarlayıp, formun yüksekliğini ve genişliğini programlama yoluyla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01204-105">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="01204-106">Visual Studio kullanıyorsanız, Windows Form Tasarımcısı kullanarak boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01204-106">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="01204-107">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms yeniden boyutlandırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="01204-107">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="01204-108">Formu programlı olarak yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="01204-108">Resize a form programmatically</span></span>

<span data-ttu-id="01204-109">Formun özelliğini ayarlayarak, çalışma zamanında formun boyutunu tanımlayın <xref:System.Windows.Forms.Form.Size%2A> .</span><span class="sxs-lookup"><span data-stu-id="01204-109">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="01204-110">Aşağıdaki kod örneği, form boyutunun 100 × 100 piksel olarak ayarlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="01204-110">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="01204-111">Form genişliğini ve yüksekliğini programsal olarak değiştirme</span><span class="sxs-lookup"><span data-stu-id="01204-111">Change form width and height programmatically</span></span>

<span data-ttu-id="01204-112">Tanımlandıktan sonra, <xref:System.Windows.Forms.Form.Size%2A> veya özelliklerini kullanarak form yüksekliğini veya genişliğini değiştirin <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="01204-112">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="01204-113">Aşağıdaki kod örneği formun sol kenarından 300 piksel olarak ayarlanan formun genişliğini gösterir, ancak yükseklik sabit kalır.</span><span class="sxs-lookup"><span data-stu-id="01204-113">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="01204-114">-veya-</span><span class="sxs-lookup"><span data-stu-id="01204-114">-or-</span></span>

<span data-ttu-id="01204-115"><xref:System.Drawing.Size.Width%2A> <xref:System.Drawing.Size.Height%2A> Özelliği ayarlayarak veya öğesini değiştirin <xref:System.Windows.Forms.Form.Size%2A> .</span><span class="sxs-lookup"><span data-stu-id="01204-115">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="01204-116">Ancak, aşağıdaki kod örneğinde gösterildiği gibi, bu yaklaşım yalnızca ayardan veya özelliklerden daha kısaktan bazılarıdır <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="01204-116">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="01204-117">Form boyutunu programsal olarak artışlarla Değiştir</span><span class="sxs-lookup"><span data-stu-id="01204-117">Change form size by increments programmatically</span></span>

<span data-ttu-id="01204-118">Formun boyutunu artırmak için <xref:System.Drawing.Size.Width%2A> ve <xref:System.Drawing.Size.Height%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="01204-118">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="01204-119">Aşağıdaki kod örneği, formun genişliğini geçerli ayarından daha geniş 200 piksel olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="01204-119">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="01204-120"><xref:System.Drawing.Size.Height%2A> <xref:System.Drawing.Size.Width%2A> <xref:System.Windows.Forms.Form.Size%2A> Özelliği yeni bir yapıya ayarlayarak aynı anda hem yükseklik hem de genişlik boyutlarını ayarlamadığınız müddetçe, her zaman bir formun boyutunu değiştirmek için veya özelliğini kullanın <xref:System.Drawing.Size> .</span><span class="sxs-lookup"><span data-stu-id="01204-120">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="01204-121"><xref:System.Windows.Forms.Form.Size%2A>Özelliği <xref:System.Drawing.Size> , bir değer türü olan bir yapı döndürür.</span><span class="sxs-lookup"><span data-stu-id="01204-121">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="01204-122">Değer türünün özelliğine yeni bir değer atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="01204-122">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="01204-123">Bu nedenle, aşağıdaki kod örneği derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="01204-123">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="01204-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01204-124">See also</span></span>

- [<span data-ttu-id="01204-125">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="01204-125">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="01204-126">Windows Forms Uygulamalarını Geliştirme</span><span class="sxs-lookup"><span data-stu-id="01204-126">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
