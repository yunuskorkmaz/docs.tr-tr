---
title: 'İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 2c31c044aa50a74255a61da1675037ab3d09f615
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053459"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma

Bu izlenecek yol, Direct3D9 içeriğinin bir Windows Presentation Foundation (WPF) uygulamasında nasıl barındıralınacağını gösterir.

Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:

- Direct3D9 içeriğini barındırmak için bir WPF projesi oluşturun.

- Direct3D9 içeriğini içeri aktarın.

- <xref:System.Windows.Interop.D3DImage> Sınıfını kullanarak Direct3D9 içeriğini görüntüleyin.

 İşiniz bittiğinde, bir WPF uygulamasında Direct3D9 içeriğini nasıl barındırabileceğinizi bilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio.

- DirectX SDK 9 veya üzeri.

- WPF uyumlu bir biçimde Direct3D9 içeriğini içeren bir DLL. Daha fazla bilgi için bkz. [WPF ve Direct3D9 birlikte](wpf-and-direct3d9-interoperation.md) çalışma ve [izlenecek yol: WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)'de barındırmak için Direct3D9 İçeriği oluşturma.

## <a name="creating-the-wpf-project"></a>WPF projesi oluşturma

İlk adım WPF uygulaması için proje oluşturmaktır.

### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için

Görsel C# adlı `D3DHost`yeni bir WPF uygulama projesi oluşturun. Daha fazla bilgi için bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.

MainWindow. xaml içinde [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]açılır.

## <a name="importing-the-direct3d9-content"></a>Direct3D9 Içeriğini içeri aktarma

Yönetilmeyen bir dll 'den Direct3D9 içeriğini `DllImport` özniteliğini kullanarak içeri aktarırsınız.

### <a name="to-import-direct3d9-content"></a>Direct3D9 içeriğini içeri aktarmak için

1. Kod düzenleyicisinde MainWindow.xaml.cs öğesini açın.

2. Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a>Direct3D9 Içeriğini barındırma

Son olarak, Direct3D9 <xref:System.Windows.Interop.D3DImage> içeriğini barındırmak için sınıfını kullanın.

### <a name="to-host-the-direct3d9-content"></a>Direct3D9 içeriğini barındırmak için

1. MainWindow. xaml içinde, otomatik olarak oluşturulan XAML 'yi aşağıdaki XAML ile değiştirin.

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. Projeyi oluşturun.

3. Direct3D9 içeriğini içeren DLL 'yi bin/Debug klasörüne kopyalayın.

4. Projeyi çalıştırmak için F5 tuşuna basın.

    Direct3D9 İçeriği WPF uygulaması içinde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
