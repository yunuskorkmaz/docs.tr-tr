---
title: 'Nasıl yapılır: UserControl Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f4055c2374103b7df941d9a9bef24ed5e6cb27c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015837"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Nasıl yapılır: UserControl Sınıfından Devralma

Bir veya daha fazla Windows Forms denetiminin işlevlerini özel kodla birleştirmek için, bir *Kullanıcı denetimi*oluşturabilirsiniz. Kullanıcı denetimleri, hızlı denetim geliştirmeyi, standart Windows Forms denetim işlevselliğini ve özel özellikler ile yöntemlerin çok yönlülüğünü birleştirir. Bir kullanıcı denetimi oluşturmaya başladığınızda, üzerinde standart Windows Forms denetimleri yerleştirebileceğiniz görünür bir tasarımcı sunulur. Bu denetimler, tüm kendi işlevlerini, ayrıca Standart denetimlerin görünüm ve davranışını (görünüm ve kullanım) korur. Bu denetimler Kullanıcı denetiminde yerleşik olduktan sonra artık kod aracılığıyla kullanılamaz. Kullanıcı denetimi kendi boyamayı yapar ve ayrıca denetimlerle ilişkili tüm temel işlevleri de işler.

## <a name="to-create-a-user-control"></a>Kullanıcı denetimi oluşturmak için

1. Visual Studio 'da yeni bir **Windows Denetim Kitaplığı** projesi oluşturun.

   Boş bir kullanıcı denetimiyle yeni bir proje oluşturulur.

2. Denetimleri **araç kutusunun** **Windows Forms** sekmesinden tasarımcı üzerine sürükleyin.

3. Bu denetimler, son kullanıcı denetiminde görünmesini istediğiniz şekilde yerleştirilmelidir ve tasarlanmalıdır. Geliştiricilerin bileşen denetimlerine erişmesine izin vermek istiyorsanız, bunları ortak olarak bildirmeniz veya yapısal denetimin özelliklerini seçmeli olarak kullanıma sunmanız gerekir. Ayrıntılar için bkz [. nasıl yapılır: Bileşen denetimlerinin](how-to-expose-properties-of-constituent-controls.md)özelliklerini kullanıma sunun.

4. Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.

5. Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın. Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
