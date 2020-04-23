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
ms.openlocfilehash: b970a5a193f82ca141c030491febce5ef352eb70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181353"
---
# <a name="msgbox-sample"></a>MsgBox Örneği
Bu örnek <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, parametre türlerini parametrelere göre ve, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, ve <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> alanlarını ne zaman kullanacağınızı gösteren bir değere göre nasıl geçirileceğini gösterir.  
  
 MsgBox örnek, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
- User32. dll dosyasından aktarılmış **MessageBox** .  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 Bu örnekte, `NativeMethods` sınıfı, `MsgBoxSample` sınıfı tarafından çağrılan her yönetilmeyen işlev için bir yönetilen prototip içerir. Yönetilen prototip yöntemleri `MsgBox` `MsgBox2`, ve `MsgBox3` aynı yönetilmeyen işlev için farklı bildirimlere sahiptir.  
  
 ANSI olarak belirtilen `MsgBox2` karakter türü, Unicode işlevinin adı olan giriş noktasıyla `MessageBoxW`eşleşmediğinden, için bildirimi ileti kutusunda yanlış çıktı üretir. `MsgBox3` Bildirimi, **entryPoint**, **charset**ve **ExactSpelling** alanları arasında bir uyumsuzluk oluşturur. Çağrıldığında bir özel `MsgBox3` durum oluşturur. Dize adlandırma ve ad sıralaması hakkında ayrıntılı bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Hazırlama](marshaling-strings.md)
- [Dizeler için Varsayılan Hazırlama](default-marshaling-for-strings.md)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [Karakter Kümesi Belirtme](specifying-a-character-set.md)
