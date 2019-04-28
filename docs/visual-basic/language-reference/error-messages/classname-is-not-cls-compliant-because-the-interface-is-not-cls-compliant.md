---
title: Uyguladığı '<classname>' arabirimi CLS uyumlu olmadığından, '<interfacename>' CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 063c42249abbfb506fd15311659599b4777d397f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649887"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>'\<SınıfAdı >' CLS uyumlu olmadığından, arabirim '\<InterfaceName >', uygular, CLS uyumlu değil
Bir sınıf veya arabirim olarak işaretlenmiş `<CLSCompliant(True)>` ne zaman türetilen veya olarak işaretlenmiş bir türün uyguladığı `<CLSCompliant(False)>` veya hiçbir işaret konulmadıysa.  
  
 Bir sınıfı veya arabirimi ile uyumlu olacak şekilde [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) tüm Devralma Hiyerarşisi olmalıdır uyumlu. Her türün devraldığı, doğrudan veya dolaylı olarak, uyumlu olması gerektiği anlamına gelir. Bir sınıf, bir veya daha fazla arabirim uygularsa, benzer şekilde, tüm bunların devralma hiyerarşilerini uyumlu olmaları gerekir.  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- CLS uyumluluğu gerektiriyorsa, bu tür içinde farklı bir devralma hiyerarşisi veya uygulama düzeni tanımlayın.  
  
- Bu tür, geçerli bir devralma hiyerarşisi veya uygulama düzeni içinde kalmasını gerektiriyorsa, kaldırma <xref:System.CLSCompliantAttribute> kendi tanımından veya olarak işaretlemek `<CLSCompliant(False)>`.  
