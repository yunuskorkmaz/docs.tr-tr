---
title: 'Nasıl yapılır: PropertyNameChanged Desenini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 01afa713e97206ea192ba55dc2affad20163f872
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665258"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Nasıl yapılır: PropertyNameChanged Desenini Uygulama
Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir *PropertyName*değiştirilen deseni bir özel denetim için. Windows Forms veri bağlama altyapısı ile kullanılan özel denetimleri uyguladığınızda bu düzeni uygulanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod örneğini derlemek için:  
  
- Kodu bir boş bir kod dosyasına yapıştırın. Özel denetim içeren bir Windows formunda kullanmalısınız bir `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama](how-to-implement-the-inotifypropertychanged-interface.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
