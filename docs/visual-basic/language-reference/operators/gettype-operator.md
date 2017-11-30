---
title: "GetType İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a>GetType İşleci (Visual Basic)
Döndürür bir <xref:System.Type> nesne belirtilen türe. <xref:System.Type> Nesne türü özellikleri, yöntemleri ve olayları gibi hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`typename`|Bilgi işlemleriniz türünün adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetType` Operatörü döndürür <xref:System.Type> için belirtilen nesne `typename`. İçinde tanımlanan tüm türünün adı geçirebilirsiniz `typename`. Buna aşağıdakiler dahildir:  
  
-   Herhangi bir Visual Basic veri türü, gibi `Boolean` veya `Date`.  
  
-   Tüm .NET Framework sınıf, yapısı, modül veya arabirimi, aşağıdaki gibi <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>.  
  
-   Tüm sınıfı, yapısı, modül veya uygulamanız tarafından tanımlanan arabirimi.  
  
-   Uygulamanız tarafından tanımlanan bir dizi.  
  
-   Uygulamanız tarafından tanımlanan herhangi bir temsilci.  
  
-   Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm numaralandırması.  
  
 Bir nesne değişkeninin türü nesnesinin almak istiyorsanız, kullanmak <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemi.  
  
 `GetType` İşleci aşağıdaki durumlarda yararlı olabilir:  
  
-   Çalışma zamanında bir türü için meta veriler erişmeniz gerekir. <xref:System.Type> Nesne türü üyeleri ve dağıtım bilgileri gibi meta veriler sağlar. Bu, örneğin, bir derlemeyi yansıtacak şekilde ihtiyacınız var. Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Aynı türde örneklerine başvurursanız görmek için iki nesne başvuruları karşılaştırmak istediğiniz. İçermiyorlarsa `GetType` aynı başvurular döndürür <xref:System.Type> nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde gösterildiği `GetType` işleci kullanılıyor.  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
