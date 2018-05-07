---
title: MsgBox Örneği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c4d38b60f349f0ecb87204cb980dd6681a8cc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="msgbox-sample"></a>MsgBox Örneği
Bu örnek parametreleri olduğu gibi değeriyle dize türleri geçirmek nasıl ve ne zaman kullanılacağı gösterilmektedir <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanları.  
  
 MsgBox örneği özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
-   **MessageBox** User32.dll dışarı.  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 Bu örnekte `LibWrap` sınıfı tarafından çağrılır her yönetilmeyen işlevi için yönetilen bir prototip içerir `MsgBoxSample` sınıfı. Yönetilen prototip yöntemleri `MsgBox`, `MsgBox2`, ve `MsgBox3` aynı için farklı bildirimleri işlevi yönetilmeyen sahip.  
  
 Bildirimi `MsgBox2` , ANSI karakter belirtildi giriş noktası ile uyumsuz olduğundan ileti kutusunda yanlış bir çıktı üretir `MessageBoxW`, Unicode işlevinin adı. Bildirimi `MsgBox3` arasında bir uyuşmazlık oluşturur **EntryPoint**, **CharSet**, ve **ExactSpelling** alanları. Çağrıldığında, `MsgBox3` bir özel durum oluşturur. Dize adlandırma ve ad hazırlama hakkında ayrıntılı bilgi için bkz: [karakter kümesini belirtme](specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizeleri Hazırlama](marshaling-strings.md)  
 [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Dizeler için Varsayılan Hazırlama](default-marshaling-for-strings.md)  
 [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)  
 [Karakter Kümesi Belirtme](specifying-a-character-set.md)
