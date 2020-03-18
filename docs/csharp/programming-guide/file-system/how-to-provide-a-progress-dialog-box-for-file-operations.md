---
title: Dosya işlemleri için ilerleme iletişim kutusu nasıl sağlanabilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705138"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Dosya işlemleri için ilerleme iletişim kutusu nasıl sağlanabilir (C# Programlama Kılavuzu)
Ad alanında <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yöntemi <xref:Microsoft.VisualBasic?displayProperty=nameWithType> kullanıyorsanız, Windows'daki dosya işlemlerinde ilerlemeyi gösteren standart bir iletişim kutusu sağlayabilirsiniz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio'da referans eklemek için  
  
1. Menü çubuğunda **Proje**, **Başvuru Ekle'yi**seçin.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
2. **Derlemeler** alanında, önceden seçilmemişse **Çerçeve'yi** seçin.  
  
3. Adlar listesinde **Microsoft.VisualBasic** onay kutusunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `sourcePath` `destinationPath` belirten dizine belirten dizin kopyaları. Bu kod, işlem bitmeden önce kalan tahmini süreyi gösteren standart bir iletişim kutusu da sağlar.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
