---
title: 'Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e48fcee8dc4c85083a00a89c88027529ab1cc3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)
Kullanıyorsanız Windows dosya işlemlerini ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilir <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yönteminde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio'da bir başvuru eklemek için  
  
1.  Menü çubuğunda seçin **proje**, **Başvuru Ekle**.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
2.  İçinde **derlemeleri** alanı seçin**Framework** tercih değil.  
  
3.  Adları listesinden seçin **Microsoft.VisualBasic** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi iletişim kutusunu kapatın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod dizine kopyalar, `sourcePath` dizine belirtir, `destinationPath` belirtir. Bu kod ayrıca işlemi tamamlanmadan önce kalan süre tahmini miktarını gösteren bir standart iletişim kutusu sağlar.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
