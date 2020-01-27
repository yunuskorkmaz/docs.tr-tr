---
title: 'Nasıl yapılır: bir dosyayla Ilişkili simgeyi ayıklama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742547"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Bir Dosyayla İlişkili Simgeyi Çıkarma
Birçok dosya, ilişkili dosya türünün görsel gösterimini sağlayan katıştırılmış simgelere sahiptir. Örneğin, Microsoft Word belgeleri bunları Word belgeleri olarak tanımlayan bir simge içerir. Bir liste denetimindeki veya tablo denetimindeki dosyaları görüntülerken, her dosya adının yanında dosya türünü temsil eden simgeyi görüntülemek isteyebilirsiniz. <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> yöntemini kullanarak bunu kolayca yapabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir dosyayla ilişkili simgenin nasıl ayıklanacağını ve dosya adını ve ilişkili simgesini bir <xref:System.Windows.Forms.ListView> denetiminde görüntülemeyi gösterir.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Örneği derlemek için:  
  
- Önceki kodu bir Windows formuna yapıştırın ve formun Oluşturucu veya <xref:System.Windows.Forms.Form.Load> olay işleme yönteminden `ExtractAssociatedIconExample` yöntemi çağırın.  
  
     Formunuzun <xref:System.IO> ad alanını içeri aktardığından emin olmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [ListView Denetimi](../controls/listview-control-windows-forms.md)
