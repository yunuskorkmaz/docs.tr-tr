---
title: 'Nasıl yapılır: Dosya Işlemleri için Ilerleme durumu Iletişim kutusu sağlama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 028e779f3cd8a17f162a79791b0c84abae14cf44
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590054"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Nasıl yapılır: Dosya Işlemleri için Ilerleme durumu Iletişim kutusu sağlama (C# Programlama Kılavuzu)
<xref:Microsoft.VisualBasic?displayProperty=nameWithType> Ad alanında <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yöntemini kullanırsanız, Windows 'daki dosya işlemlerinde ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilirsiniz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio 'da bir başvuru eklemek için  
  
1. Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
2. **Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.  
  
3. Ad listesinde, **Microsoft. VisualBasic** onay kutusunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `sourcePath` belirten dizinini belirten `destinationPath` dizine kopyalar. Bu kod ayrıca, işlem tamamlanmadan önce kalan tahmini süreyi gösteren standart bir iletişim kutusu sağlar.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
