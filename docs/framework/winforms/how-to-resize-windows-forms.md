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
# <a name="how-to-resize-windows-forms"></a>Nasıl yapılır: Windows Forms’u Yeniden Boyutlandırma

Windows formunuzun boyutunu birkaç şekilde belirtebilirsiniz. Özelliği için yeni bir değer ayarlayarak <xref:System.Windows.Forms.Form.Size%2A> ya da <xref:System.Windows.Forms.Control.Height%2A> veya <xref:System.Windows.Forms.Control.Width%2A> özelliklerini ayrı ayrı ayarlayıp, formun yüksekliğini ve genişliğini programlama yoluyla değiştirebilirsiniz. Visual Studio kullanıyorsanız, Windows Form Tasarımcısı kullanarak boyutunu değiştirebilirsiniz. Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms yeniden boyutlandırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Formu programlı olarak yeniden boyutlandırma

Formun özelliğini ayarlayarak, çalışma zamanında formun boyutunu tanımlayın <xref:System.Windows.Forms.Form.Size%2A> .

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

Tanımlandıktan sonra, <xref:System.Windows.Forms.Form.Size%2A> veya özelliklerini kullanarak form yüksekliğini veya genişliğini değiştirin <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> .

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

-veya-

<xref:System.Drawing.Size.Width%2A> <xref:System.Drawing.Size.Height%2A> Özelliği ayarlayarak veya öğesini değiştirin <xref:System.Windows.Forms.Form.Size%2A> .

Ancak, aşağıdaki kod örneğinde gösterildiği gibi, bu yaklaşım yalnızca ayardan veya özelliklerden daha kısaktan bazılarıdır <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> .

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
> <xref:System.Drawing.Size.Height%2A> <xref:System.Drawing.Size.Width%2A> <xref:System.Windows.Forms.Form.Size%2A> Özelliği yeni bir yapıya ayarlayarak aynı anda hem yükseklik hem de genişlik boyutlarını ayarlamadığınız müddetçe, her zaman bir formun boyutunu değiştirmek için veya özelliğini kullanın <xref:System.Drawing.Size> . <xref:System.Windows.Forms.Form.Size%2A>Özelliği <xref:System.Drawing.Size> , bir değer türü olan bir yapı döndürür. Değer türünün özelliğine yeni bir değer atayamazsınız. Bu nedenle, aşağıdaki kod örneği derlenmeyecektir.

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
