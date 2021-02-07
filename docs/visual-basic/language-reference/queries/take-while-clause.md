---
description: 'Şu konuda daha fazla bilgi edinin: Take While tümcesi (Visual Basic)'
title: Take While Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: a413223d4a85670c66f71e24addb92ae4d38a4a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719714"
---
# <a name="take-while-clause-visual-basic"></a>Take While Tümcesi (Visual Basic)

Belirtilen koşul olduğu `true` ve kalan öğeleri atlayan sürece bir koleksiyondaki öğeleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Süre|Tanım|  
|---|---|  
|`expression`|Gereklidir. İçin öğeleri test eden bir koşulu temsil eden bir ifade. İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .|  
  
## <a name="remarks"></a>Açıklamalar  

 `Take While`Yan tümcesi, sağlanan dönüşceye kadar bir sorgu sonucunun başından alınan öğeleri içerir `expression` `false` . `expression`Döndürmeden sonra `false` sorgu kalan tüm öğeleri atlar. `expression`Kalan sonuçlar için yok sayılır.  
  
 Yan tümcesi, `Take While` belirli bir `Where` `Where` koşulu karşılayan bir sorgudaki tüm öğeleri dahil etmek için kullanılan yan tümcesinden farklıdır. `Take While`Yan tümcesi yalnızca koşul karşılanmadığı sürece öğeleri içerir. `Take While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, `Take While` bir sipariş olmadan ilk müşteri bulunana kadar sonuçları almak için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Take Yan Tümcesi](take-clause.md)
- [Skip While Yan Tümcesi](skip-while-clause.md)
- [WHERE yan tümcesi](where-clause.md)
