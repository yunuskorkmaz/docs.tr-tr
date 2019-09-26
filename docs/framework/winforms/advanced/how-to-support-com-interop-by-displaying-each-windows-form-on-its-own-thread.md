---
title: 'Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306384"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Nasıl yapılır: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme

Formunuzu, <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemini kullanarak oluşturabileceğiniz bir .NET Framework ileti döngüsünde görüntüleyerek com birlikte çalışabilirlik sorunlarını çözebilirsiniz.

Bir Windows formunun bir COM istemci uygulamasından düzgün çalışmasını sağlamak için, formu bir Windows Forms ileti döngüsünde çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:

- Windows formunu göstermek için yönteminikullanın.<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Daha fazla bilgi için [nasıl yapılır: ShowDialog yöntemi](com-interop-by-displaying-a-windows-form-shadow.md)Ile bir WINDOWS formunu görüntüleyerek com birlikte çalışabilirliğine destek.

- Her Windows formunu ayrı bir iş parçacığında görüntüleyin.

Visual Studio 'da bu özellik için kapsamlı destek vardır.

Ayrıca bkz [. İzlenecek yol: Her bir Windows formunu kendi Iş parçacığında](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))görüntüleyerek com birlikte çalışmasını destekleme.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, formun ayrı bir iş parçacığında nasıl görüntüleneceğini ve bu iş parçacığında bir Windows Forms <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> ileti göndericisi başlatmak için yöntemini çağırmayı gösterir. Bu yaklaşımı kullanmak için, <xref:System.Windows.Forms.Control.Invoke%2A> yöntemini kullanarak yönetilmeyen uygulamadan forma yapılan tüm çağrıları sıramalısınız.

Bu yaklaşım, bir formun her örneğinin kendi iş parçacığında kendi ileti döngüsü kullanılarak çalışmasını gerektirir. İş parçacığı başına birden fazla ileti döngüsü çalıştırıyor olabilirsiniz. Bu nedenle, istemci uygulamanın ileti döngüsünü değiştiremezsiniz. Ancak, .NET Framework bileşenini kendi ileti döngüsünü kullanan yeni bir iş parçacığını başlatacak şekilde değiştirebilirsiniz.

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a>Kod derleme

, Ve türlerini adlı bir`COMWinform.dll`derlemedederleyin. `FormManager` `Form1` `COMForm` Com [Için derleme paketleme](../../interop/packaging-an-assembly-for-com.md)bölümünde açıklanan yöntemlerden bırını kullanarak com birlikte çalışması için derlemeyi kaydettirin. Artık derlemeyi ve buna karşılık gelen tür kitaplığı (. tlb) dosyasını yönetilmeyen uygulamalarda kullanabilirsiniz. Örneğin, tür kitaplığını Visual Basic 6,0 yürütülebilir bir projede başvuru olarak kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Bileşenlerini COM'da Gösterme](../../interop/exposing-dotnet-components-to-com.md)
- [COM için Bütünleştirilmiş Kod Paketleme](../../interop/packaging-an-assembly-for-com.md)
- [Bütünleştirilmiş Kodları COM ile Kaydetme](../../interop/registering-assemblies-with-com.md)
- [Nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışmasını destekleme](com-interop-by-displaying-a-windows-form-shadow.md)
- [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](windows-forms-and-unmanaged-applications-overview.md)
