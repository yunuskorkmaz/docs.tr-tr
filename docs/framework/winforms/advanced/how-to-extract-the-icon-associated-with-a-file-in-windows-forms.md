---
title: 'Nasıl yapılır: Windows Forms’da Bir Dosyayla İlişkili Simgeyi Çıkarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: d754dc5e8a57b3c4e2e5439bb2524a22d44813c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112560"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Nasıl yapılır: Windows Forms’da Bir Dosyayla İlişkili Simgeyi Çıkarma
Çok sayıda dosya sağlayan bir görsel bir temsili ilişkili dosya türü simgeleri katıştırılmış sahip. Örneğin, Microsoft Word belgeleri, bunları Word belgeleri olarak tanımlayan bir simge içerir. Liste denetimi ya da tablo denetim dosyaları görüntülerken, her dosya adının yanındaki dosya türünü temsil eden bir simge görüntülemek isteyebilirsiniz. Kolayca kullanarak bunu yapabilirsiniz <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir dosyayla ilişkili simgeyi çıkarma ve görüntü dosya adı ve ilgili simgeye yapmayı gösteren bir <xref:System.Windows.Forms.ListView> denetimi.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örneği derlemek için:  
  
-   Yukarıdaki kod, bir Windows Form ve çağrı yapıştırın `ExtractAssociatedIconExample` formun oluşturucudan yöntemi veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.  
  
     Formunuza alındığından emin olmak ihtiyacınız olacak <xref:System.IO> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [ListView Denetimi](../controls/listview-control-windows-forms.md)
