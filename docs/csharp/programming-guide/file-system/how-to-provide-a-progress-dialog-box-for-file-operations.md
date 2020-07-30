---
title: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama-C# Programlama Kılavuzu
description: Dosya işlemleri için CopyFile (dize, dize, UIOption) yöntemi kullanılarak bir ilerleme durumu iletişim kutusu sağlamayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 2ea18d924b47fc10412d37479f1b09f7eef7ad3b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301976"
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
