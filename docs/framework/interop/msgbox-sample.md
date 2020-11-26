---
title: MsgBox Örneği
description: String türlerini, MsgBox kullanarak parametrelere göre değerlere göre geçirme örneğine bakın. .NET 'teki EntryPoint, CharSet ve ExactSpelling alanlarının ne zaman kullanılacağını gösterir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: 024ed612115ce73646596651fe454238418446db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242025"
---
# <a name="msgbox-sample"></a>MsgBox Örneği

Bu örnek, parametre türlerini parametrelere göre ve,, ve alanlarını ne zaman kullanacağınızı gösteren bir değere göre nasıl geçirileceğini gösterir <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint> <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> .  
  
 MsgBox örnek, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
- User32.dll 'den dışarıya aktarılmış **MessageBox** .  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 Bu örnekte, sınıfı, `NativeMethods` sınıfı tarafından çağrılan her yönetilmeyen işlev için bir yönetilen prototip içerir `MsgBoxSample` . Yönetilen prototip yöntemleri, `MsgBox` `MsgBox2` ve `MsgBox3` aynı yönetilmeyen işlev için farklı bildirimlere sahiptir.  
  
 `MsgBox2`ANSI olarak belirtilen karakter türü, Unicode işlevinin adı olan giriş noktasıyla eşleşmediğinden, için bildirimi ileti kutusunda yanlış çıktı üretir `MessageBoxW` . Bildirimi, `MsgBox3` **entryPoint**, **charset** ve **ExactSpelling** alanları arasında bir uyumsuzluk oluşturur. Çağrıldığında `MsgBox3` bir özel durum oluşturur. Dize adlandırma ve ad sıralaması hakkında ayrıntılı bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).  
  
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
