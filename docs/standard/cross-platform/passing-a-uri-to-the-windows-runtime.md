---
title: URI'yı Windows Çalışma Zamanı'na Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: 71d427c2d602efbd92dc0128b1fada85a987904a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123629"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>URI'yı Windows Çalışma Zamanı'na Geçirme
Windows Çalışma Zamanı yöntemler yalnızca mutlak URI 'Leri kabul eder. Bir Windows Çalışma Zamanı yöntemine göreli bir URI geçirirseniz, bir <xref:System.ArgumentException> özel durumu oluşturulur. İşte bu nedenle, .NET Framework kodda Windows Çalışma Zamanı kullandığınızda <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı IntelliSense içinde <xref:System.Uri?displayProperty=nameWithType> olarak görünür. <xref:System.Uri?displayProperty=nameWithType> sınıfı göreli URI 'Lere izin veriyor, ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı değil. Bu Ayrıca, Windows Çalışma Zamanı bileşenlerinde kullanıma sunabileceğiniz yöntemler için de geçerlidir. Bileşeniniz URI alan bir yöntemi kullanıma sunarsa, kodunuzdaki imza <xref:System.Uri?displayProperty=nameWithType>içerir. Ancak, bileşeninizin kullanıcıları için imza <xref:Windows.Foundation.Uri?displayProperty=nameWithType>içerir. Bileşeninizin geçirildiği bir URI mutlak bir URI olmalıdır.  
  
Bu konu, bir mutlak URI 'nin nasıl algılanacağını ve uygulama paketindeki bir kaynağa başvururken nasıl oluşturulacağını gösterir.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Mutlak bir URI algılama ve kullanma  
Bir URI 'nin Windows Çalışma Zamanı geçirmeden önce mutlak olduğundan emin olmak için <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> özelliğini kullanın. Bu özelliği kullanmak, <xref:System.ArgumentException> özel durumunun yakalanından ve işlenenden daha etkilidir.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Uygulama paketindeki bir kaynak için mutlak URI kullanma  
Uygulama paketinizin içerdiği bir kaynak için bir URI belirtmek istiyorsanız, mutlak bir URI oluşturmak için `ms-appx` veya `ms-appx-web` düzenini kullanabilirsiniz.  
  
Aşağıdaki örnek, hem XAML hem de kod kullanarak bir <xref:Windows.UI.Xaml.Controls.WebView> denetimi için <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> özelliğinin ve sayfalar adlı bir klasörde bulunan kaynaklara <xref:Windows.UI.Xaml.Controls.Image.Source%2A> <xref:Windows.UI.Xaml.Controls.Image> özelliği için nasıl ayarlanacağını gösterir.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Bu şemalar hakkında daha fazla bilgi için bkz. Windows Geliştirme Merkezi 'nde [URI düzenleri](/windows/uwp/app-resources/uri-schemes) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
