---
title: Formu yeniden boyutlandır
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739310"
---
# <a name="how-to-resize-windows-forms"></a>Nasıl yapılır: Windows Formlarını Yeniden Boyutlandırma

Windows formunuzun boyutunu birkaç şekilde belirtebilirsiniz. <xref:System.Windows.Forms.Form.Size%2A> özelliği için yeni bir değer ayarlayarak ya da <xref:System.Windows.Forms.Control.Height%2A> veya <xref:System.Windows.Forms.Control.Width%2A> özelliklerini ayrı ayrı ayarlayarak formun yüksekliğini ve genişliğini programlama yoluyla değiştirebilirsiniz. Visual Studio kullanıyorsanız, Windows Form Tasarımcısı kullanarak boyutunu değiştirebilirsiniz. Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms yeniden boyutlandırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Formu programlı olarak yeniden boyutlandırma

Formun <xref:System.Windows.Forms.Form.Size%2A> özelliğini ayarlayarak, çalışma zamanında formun boyutunu tanımlayın.

Aşağıdaki kod örneği, form boyutunun 100 × 100 piksel olarak ayarlandığını gösterir.

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>Form genişliğini ve yüksekliğini programsal olarak değiştirme

<xref:System.Windows.Forms.Form.Size%2A> tanımlandıktan sonra, <xref:System.Windows.Forms.Control.Width%2A> veya <xref:System.Windows.Forms.Control.Height%2A> özelliklerini kullanarak form yüksekliğini veya genişliğini değiştirin.

Aşağıdaki kod örneği formun sol kenarından 300 piksel olarak ayarlanan formun genişliğini gösterir, ancak yükseklik sabit kalır.

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

veya

<xref:System.Windows.Forms.Form.Size%2A> özelliğini ayarlayarak <xref:System.Drawing.Size.Width%2A> veya <xref:System.Drawing.Size.Height%2A> değiştirin.

Bununla birlikte, aşağıdaki kod örneğinde gösterildiği gibi, bu yaklaşım yalnızca <xref:System.Windows.Forms.Control.Width%2A> veya <xref:System.Windows.Forms.Control.Height%2A> özelliklerden daha kısaktan bazılarıdır.

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>Form boyutunu programsal olarak artışlarla Değiştir

Formun boyutunu artırmak için <xref:System.Drawing.Size.Width%2A> ve <xref:System.Drawing.Size.Height%2A> özelliklerini ayarlayın.

Aşağıdaki kod örneği, formun genişliğini geçerli ayarından daha geniş 200 piksel olarak gösterir.

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
> Her zaman bir formun boyutunu değiştirmek için <xref:System.Drawing.Size.Height%2A> veya <xref:System.Drawing.Size.Width%2A> özelliğini kullanın. Bu, <xref:System.Windows.Forms.Form.Size%2A> özelliğini yeni bir <xref:System.Drawing.Size> yapısı olarak ayarlayarak hem yükseklik hem de genişlik boyutlarını aynı anda ayarlamadığınız müddetçe. <xref:System.Windows.Forms.Form.Size%2A> özelliği, bir değer türü olan bir <xref:System.Drawing.Size> yapısı döndürür. Değer türünün özelliğine yeni bir değer atayamazsınız. Bu nedenle, aşağıdaki kod örneği derlenmeyecektir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
- [Windows Forms Uygulamalarını Geliştirme](./advanced/index.md)
