---
title: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705138"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama (C# Programlama Kılavuzu)
<xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanında <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yöntemini kullanırsanız, Windows 'daki dosya işlemlerinde ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilirsiniz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio 'da bir başvuru eklemek için  
  
1. Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
2. **Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.  
  
3. Ad listesinde, **Microsoft. VisualBasic** onay kutusunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `sourcePath` belirten dizini `destinationPath` tarafından belirtilen dizine kopyalar. Bu kod ayrıca, işlem tamamlanmadan önce kalan tahmini süreyi gösteren standart bir iletişim kutusu sağlar.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
