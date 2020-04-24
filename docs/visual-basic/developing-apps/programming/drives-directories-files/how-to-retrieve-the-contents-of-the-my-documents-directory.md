---
title: 'Nasıl Yapılır: Belgelerim Dizini İçeriğini Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: cf4470020507c581999b9d72602ddb6e3e76ed74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334529"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma

<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesnesi, **Belgelerim** veya **masaüstlerim**gibi **tüm Kullanıcı** dizinlerinden okumak için kullanılabilir.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Belgelerim klasöründen okumak için  
  
- Belirli bir `ReadAllText` dizindeki her bir dosyanın metnini okumak için yöntemini kullanın. Aşağıdaki kod, bir dizini ve dosyayı belirtir ve sonra bunları `ReadAllText` adlı `patients`dizeye okumak için kullanır.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
