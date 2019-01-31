---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282600"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır
Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken. İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tedarik bir `PathName` işlev çağrısında bağımsız değişken.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
