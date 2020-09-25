---
title: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama-C# Programlama Kılavuzu
description: Dosya işlemleri için CopyFile (dize, dize, UIOption) yöntemi kullanılarak bir ilerleme durumu iletişim kutusu sağlamayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 5d16aeb3a5394ca250e4a5e26074db797c54216d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185892"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama (C# Programlama Kılavuzu)

Ad alanında yöntemini kullanırsanız, Windows 'daki dosya işlemlerinde ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilirsiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> <xref:Microsoft.VisualBasic?displayProperty=nameWithType> .  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio 'da bir başvuru eklemek için  
  
1. Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
2. **Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.  
  
3. Ad listesinde, **Microsoft. VisualBasic** onay kutusunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, belirten dizinini belirten `sourcePath` dizine kopyalar `destinationPath` . Bu kod ayrıca, işlem tamamlanmadan önce kalan tahmini süreyi gösteren standart bir iletişim kutusu sağlar.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
