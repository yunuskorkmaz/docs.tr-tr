---
title: 'Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 654bfec4e8ba163c9dc9adf470c45401c0babd8b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme
Bu belge, bir alt görevin üst göreve eklenmesini önleme gösterilmiştir. Bir üçüncü taraf tarafından yazılmış ve görevleri de kullanan bir bileşen çağırdığınızda alt görevin üst göreve eklenmesini önleme yararlı olur. Örneğin, kullanan bir üçüncü taraf bileşen <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> oluşturmak için seçeneği bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesne sorunlara neden olabilir, kodunuzda uzun süre çalışan ise veya işlenmeyen bir özel durum oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir alt görevin üst göreve eklenmesini önleme etkileri için varsayılan seçenekleri kullanarak etkilerini karşılaştırır. Örnekte bir <xref:System.Threading.Tasks.Task> de kullanan bir üçüncü taraf kitaplık içine çağıran nesne bir <xref:System.Threading.Tasks.Task> nesnesi. Üçüncü taraf kitaplığını kullanan <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> oluşturmak için seçeneği <xref:System.Threading.Tasks.Task> nesnesi. Uygulamanın kullandığı <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst görev oluşturmak için seçeneği. Bu seçenek kaldırmak için çalışma zamanı bildirir <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> alt görevler belirtiminde.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Tüm alt görevler tamamlanana kadar üst göreve tamamlanmıyor olduğundan, uzun süre çalışan alt görevin kötü gerçekleştirmek genel uygulama neden olabilir. Uygulama üst görevi oluşturmak için varsayılan seçenekleri kullandığında üst görev tamamlanmadan önce bu örnekte, alt görevin bitmesi gerekir. Uygulama kullandığında <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst, alt seçeneği bağlı değil. Bu nedenle, uygulama üst görev tamamlandıktan sonra ve alt görevin tamamlanmasını beklemeniz gerekir önce ek iş gerçekleştirebilirsiniz.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DenyChildAttach.cs` (`DenyChildAttach.vb` Visual Basic), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe DenyChildAttach.cs**  
  
 Visual Basic  
  
 **Vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
