---
title: Çalıştırılabilir örnekleri algılama dönemi
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 9652dd811f64e5324219b8aa0700ab8219edeeb0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709715"
---
# <a name="runnable-instances-detection-period"></a>Çalıştırılabilir örnekleri algılama dönemi
SQL iş akışı örneği Store düzenli olarak çalıştırılabilir veya etkinleştirilebilir örnekleri Kalıcılık veritabanında algılar ve uyanır bir iç görev çalıştırır. **Çalıştırılabilir örnekleri algılama dönemi** SQL iş akışı örneği Store özelliği SQL iş akışı örneği Store sonra çalıştırılabilir veya etkinleştirilebilir akışlarınızın algılamak için algılama görev çalıştırır süreyi belirtir Önceki saptama döngüsünden sonra Kalıcılık veritabanı örnekleri.  
  
 Bu özellik için daha kısa bir aralık ayarını örneğinin sonraki yükleniyor ve olay'nın sinyal ve bir iş akışı örneği ile ilişkili bir zamanlayıcı süre sonu arasındaki süreyi azaltır. Ancak, ayrıca bir ana bilgisayar üzerindeki işlem yükü artırır ve dayanıklı zamanlayıcılar ve/veya ana bilgisayar hataları nadir olduğu senaryolarda istenmeyebilir. Özelliğin türü TimeSpan ve özelliğinin değeri biçimdedir: ss. Bu özellik için en düşük değer 00:00:01 ' dir. Bir özellik için varsayılan değer 00:00:05 ' dir.  
  
 Daha fazla bilgi için bkz: algılama ve çalıştırılabilir ve etkinleştirilebilir iş akışı örnekleri, etkinleştirme [örnek etkinleştirme](instance-activation.md).
