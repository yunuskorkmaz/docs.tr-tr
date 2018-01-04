---
title: "Nasıl yapılır: Windows Formlarında Bir Dosyayla İlişkili Simgeyi Çıkarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5153f6389c4477a18c647d7cdaf7b49b43bb7ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Bir Dosyayla İlişkili Simgeyi Çıkarma
Çok sayıda dosya ilişkili dosya türü için görsel bir sunumdur sağlamak simgeler katıştırılmış. Örneğin, Microsoft Word belgelerini Word belgeleri olarak belirten bir simge içerir. Dosyaları bir liste denetimini veya tablo denetim görüntülerken, her dosya adının yanındaki dosya türünü temsil eden simgeyi görüntülemek isteyebilirsiniz. Kolayca kullanarak bunu yapabilirsiniz <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir dosyayla ilişkili simgeyi çıkarma ve dosya adını ve ilişkili simgesini görüntülemek nasıl gösteren bir <xref:System.Windows.Forms.ListView> denetim.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek derlemek için:  
  
-   Önceki kod bir Windows formu, arama yapıştırın ve `ExtractAssociatedIconExample` formun Oluşturucusu yönteminden veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.  
  
     Formunuz alındığından emin olmak gerekir <xref:System.IO> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
