---
title: Uyguladığı '<classname>' arabirimi CLS uyumlu olmadığından, '<interfacename>' CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: a482d14094a3fa86b56ca84af46c45e6093416c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874634"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>Uyguladığı '\<classname>' arabirimi CLS uyumlu olmadığından, '\<interfacename>' CLS uyumlu değil

Bir sınıf veya arabirim, `<CLSCompliant(True)>` veya olarak işaretlenen veya işaretlenmemiş bir türden türetildiklerinde olarak işaretlenir `<CLSCompliant(False)>` .  
  
 Bir sınıfın veya arabirimin [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, tüm devralma hiyerarşisinin uyumlu olması gerekir. Bu, devralınan her türün doğrudan veya dolaylı olarak uyumlu olması anlamına gelir. Benzer şekilde, bir sınıf bir veya daha fazla arabirim uygularsa bunların tümünün devralma hiyerarşileri boyunca uyumlu olmaları gerekir.  
  
 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.  
  
 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- CLS uyumluluğu gerekiyorsa, bu türü farklı bir devralma hiyerarşisi veya uygulama şeması içinde tanımlayın.  
  
- Bu türün geçerli devralma hiyerarşisinde veya uygulama düzeninde kalmasını istiyorsanız, ' ın <xref:System.CLSCompliantAttribute> tanımını kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .  
