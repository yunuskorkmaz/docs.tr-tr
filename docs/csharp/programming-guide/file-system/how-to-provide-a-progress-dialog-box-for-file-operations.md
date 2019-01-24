---
title: 'Nasıl yapılır: Dosya işlemleri için - ilerleme durumu iletişim kutusu sağlar C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: ab268c30af6b5eefe84ade852c679535c1e48068
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597274"
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
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
