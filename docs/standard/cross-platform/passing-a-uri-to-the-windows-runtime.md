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
ms.openlocfilehash: 7152fb02abf430c0d0e27b82550e4006e3958e93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288894"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>URI'yı Windows Çalışma Zamanı'na Geçirme
Windows Çalışma Zamanı yöntemler yalnızca mutlak URI 'Leri kabul eder. Bir Windows Çalışma Zamanı yöntemine göreli bir URI geçirirseniz, bir <xref:System.ArgumentException> özel durum oluşturulur. Neden: Windows Çalışma Zamanı .NET Framework kodda kullandığınızda, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıf <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde olarak görünür. <xref:System.Uri?displayProperty=nameWithType>Sınıfı göreli URI 'lere izin verir, ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı desteklemez. Bu Ayrıca, Windows Çalışma Zamanı bileşenlerinde kullanıma sunabileceğiniz yöntemler için de geçerlidir. Bileşeniniz URI alan bir yöntemi kullanıma sunarsa, kodunuzdaki imza dahil değildir <xref:System.Uri?displayProperty=nameWithType> . Ancak, bileşeninizin kullanıcıları için imza şunları içerir <xref:Windows.Foundation.Uri?displayProperty=nameWithType> . Bileşeninizin geçirildiği bir URI mutlak bir URI olmalıdır.  
  
Bu konu, bir mutlak URI 'nin nasıl algılanacağını ve uygulama paketindeki bir kaynağa başvururken nasıl oluşturulacağını gösterir.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Mutlak bir URI algılama ve kullanma  
<xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>BIR URI 'nin Windows çalışma zamanı geçirmeden önce mutlak olduğundan emin olmak için özelliğini kullanın. Bu özelliği kullanmak, özel durumu yakalama ve işlemeye kıyasla daha etkilidir <xref:System.ArgumentException> .  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Uygulama paketindeki bir kaynak için mutlak URI kullanma  
Uygulama paketinizin içerdiği bir kaynak için bir URI belirtmek istiyorsanız, `ms-appx` veya `ms-appx-web` düzenini kullanarak mutlak bir URI oluşturabilirsiniz.  
  
Aşağıdaki örnek, <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> <xref:Windows.UI.Xaml.Controls.WebView> <xref:Windows.UI.Xaml.Controls.Image.Source%2A> <xref:Windows.UI.Xaml.Controls.Image> hem XAML hem de kod kullanarak, bir denetimin özelliğinin ve sayfalar adlı bir klasörde bulunan kaynaklar için nasıl ayarlanacağını gösterir.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Bu şemalar hakkında daha fazla bilgi için bkz. Windows Geliştirme Merkezi 'nde [URI düzenleri](/windows/uwp/app-resources/uri-schemes) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](support-for-windows-store-apps-and-windows-runtime.md)
