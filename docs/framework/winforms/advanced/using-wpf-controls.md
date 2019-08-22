---
title: WPF Denetimlerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658495"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Windows Forms uygulamalarında WPF denetimlerini kullanma

Windows Forms tabanlı uygulamalarda Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz. Bunlar iki farklı görünüm teknolojisidir, ancak sorunsuz bir şekilde çalışır.

Visual Studio 'daki Windows Form Tasarımcısı, Windows Presentation Foundation denetimleri barındırmak için görsel tasarım ortamı sağlar. WPF denetimi, adında <xref:System.Windows.Forms.Integration.ElementHost>özel bir Windows Forms denetimi tarafından barındırılır. Bu denetim WPF denetiminin formun düzenine katılmasını ve klavye ve fare iletilerini almasını sağlar. Tasarım zamanında, <xref:System.Windows.Forms.Integration.ElementHost> her türlü Windows Forms denetimi yaptığınız gibi denetimi düzenleyebilirsiniz.

WPF tabanlı uygulamalarda Windows Forms denetimlerini de kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Ayrıca bkz.

- [WPF ve Windows Forms birlikte çalışma](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)
