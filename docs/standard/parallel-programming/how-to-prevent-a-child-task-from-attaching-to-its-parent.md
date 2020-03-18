---
title: 'Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 265b6d06f17a1dfbee3f009feff1ee1645e62a46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139254"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme
Bu belge, alt görevin üst göreve eklenmesini nasıl önleyeceğini gösterir. Bir alt görevin üst öğesine eklenmesini engellemek, üçüncü bir taraftarafından yazılmış ve görevleri de kullanan bir bileşeni çağırdığınızda yararlıdır. Örneğin, bir veya <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> nesne oluşturmak için seçeneği kullanan bir üçüncü taraf bileşeni, uzun süredir çalışıyorsa veya işlenmemiş bir özel durum atarsa, kodunuzda sorunlara neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, varsayılan seçenekleri kullanmanın etkileriyle, bir alt görevin üst öğeye eklenmesini engellemenin etkileri karşılaştırılır. Örnek, bir <xref:System.Threading.Tasks.Task> nesneyi de kullanan bir üçüncü taraf <xref:System.Threading.Tasks.Task> kitaplığa çağıran bir nesne oluşturur. Üçüncü taraf kitaplığı <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> <xref:System.Threading.Tasks.Task> nesneyi oluşturmak için seçeneği kullanır. Uygulama üst <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> görevi oluşturmak için seçeneği kullanır. Bu seçenek, alt görevlerdeki <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> belirtimi kaldırmak için çalışma zamanı bildirir.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Bir üst görev tüm alt görevler bitene kadar bitmedığından, uzun süren bir alt görev genel uygulamanın kötü performans göstermesine neden olabilir. Bu örnekte, uygulama üst görevi oluşturmak için varsayılan seçenekleri kullandığında, alt görev üst görev bitmeden önce bitirmelidir. Uygulama <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneği kullandığında, alt öğe üst öğeye bağlı değildir. Bu nedenle, uygulama üst görev bittikten sonra ve alt görevin tamamlanmasını beklemeden önce ek iş gerçekleştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
