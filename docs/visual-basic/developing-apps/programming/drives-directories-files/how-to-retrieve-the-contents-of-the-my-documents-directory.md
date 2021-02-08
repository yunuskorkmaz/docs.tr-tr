---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic Belgelerim dizininin Içeriğini alma'
title: 'Nasıl yapılır: Belgelerim Dizini İçeriğini Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: e9e6ffc202332bd8d1849ef886fd4e7d6cc46a54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797399"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma

<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>Nesnesi, **Belgelerim veya Masaüstlerim** gibi **tüm Kullanıcı** dizinlerinden okumak için kullanılabilir.   
  
### <a name="to-read-from-the-my-documents-folder"></a>Belgelerim klasöründen okumak için  
  
- `ReadAllText`Belirli bir dizindeki her bir dosyanın metnini okumak için yöntemini kullanın. Aşağıdaki kod, bir dizini ve dosyayı belirtir ve sonra `ReadAllText` bunları adlı dizeye okumak için kullanır `patients` .  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
