---
title: '&#39;Dir&#39; işlevi önce çağrılmalıdır ile bir &#39;PathName&#39; bağımsız değişken'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: f7e9ef9cc6309f24ae9f8963e910b41180c029b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518494"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39; işlevi önce çağrılmalıdır ile bir &#39;PathName&#39; bağımsız değişken
Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken. İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tedarik bir `PathName` işlev çağrısında bağımsız değişken.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
