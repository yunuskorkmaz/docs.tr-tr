---
title: 'Nasıl yapılır: Dosya işlemleri için - ilerleme durumu iletişim kutusu sağlar C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 462da68313fea19e5b89a9e2f5221f6659338e98
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975049"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Nasıl yapılır: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama (C# Programlama Kılavuzu)
Kullanırsanız Windows'da dosya işlemlerinin Windows içinde ilerleme durumunu gösteren standart iletişim kutusunu sağlayabilirsiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yönteminde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio'da bir başvuru eklemek için  
  
1.  Menü çubuğunda, **proje**, **Başvuru Ekle**.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
2.  İçinde **derlemeleri** alanında seçin **Framework** tercih değildir.  
  
3.  Adları listesinde seçin **Microsoft.VisualBasic** onay kutusunu işaretleyin ve ardından **Tamam** iletişim kutusunu kapatmak için düğme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu belirtilen dizine kopyalar, `sourcePath` dizini, `destinationPath` belirtir. Bu kod Ayrıca işlem tamamlanmadan önce zaman kalan tahmini süreyi gösteren standart iletişim kutusunu sağlar.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
