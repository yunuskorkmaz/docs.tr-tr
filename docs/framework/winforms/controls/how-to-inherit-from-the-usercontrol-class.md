---
title: 'Nasıl yapılır: UserControl Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10bb807d012a130ad633b7ce06f99c5abf2cdda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458362"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Nasıl yapılır: UserControl Sınıfından Devralma

Bir veya daha fazla Windows Forms denetiminin işlevlerini özel kodla birleştirmek için, bir *Kullanıcı denetimi*oluşturabilirsiniz. Kullanıcı denetimleri, hızlı denetim geliştirmeyi, standart Windows Forms denetim işlevselliğini ve özel özellikler ile yöntemlerin çok yönlülüğünü birleştirir. Bir kullanıcı denetimi oluşturmaya başladığınızda, üzerinde standart Windows Forms denetimleri yerleştirebileceğiniz görünür bir tasarımcı sunulur. Bu denetimler, tüm kendi işlevlerini, ayrıca Standart denetimlerin görünüm ve davranışını (görünüm ve kullanım) korur. Bu denetimler Kullanıcı denetiminde yerleşik olduktan sonra artık kod aracılığıyla kullanılamaz. Kullanıcı denetimi kendi boyamayı yapar ve ayrıca denetimlerle ilişkili tüm temel işlevleri de işler.

## <a name="to-create-a-user-control"></a>Kullanıcı denetimi oluşturmak için

1. Visual Studio 'da yeni bir **Windows Denetim Kitaplığı** projesi oluşturun.

   Boş bir kullanıcı denetimiyle yeni bir proje oluşturulur.

2. Denetimleri **araç kutusunun** **Windows Forms** sekmesinden tasarımcı üzerine sürükleyin.

3. Bu denetimler, son kullanıcı denetiminde görünmesini istediğiniz şekilde yerleştirilmelidir ve tasarlanmalıdır. Geliştiricilerin bileşen denetimlerine erişmesine izin vermek istiyorsanız, bunları ortak olarak bildirmeniz veya yapısal denetimin özelliklerini seçmeli olarak kullanıma sunmanız gerekir. Ayrıntılar için bkz. [nasıl yapılır: yapısal denetimlerin özelliklerini kullanıma](how-to-expose-properties-of-constituent-controls.md)sunma.

4. Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.

5. Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın. Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Denetim Sınıfından Devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms için Denetimler Yazma](how-to-author-controls-for-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
