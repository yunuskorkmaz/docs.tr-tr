---
title: 'Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212481"
---
# <a name="how-to-use-resources-in-localizable-apps"></a>Nasıl yapılır: yerelleştirilebilir uygulamalarda kaynakları kullanma

Yerelleştirme, bir kullanıcı arabirimini farklı kültürlere uyarlayacağı anlamına gelir. Bunu yapmak için başlıklar, açıklamalı alt yazılar ve liste kutusu öğeleri gibi metinler çevrilmelidir. Çeviriyi daha kolay hale getirmek için çevrilecek öğeler kaynak dosyalarına toplanır. Yerelleştirme için bir kaynak dosyası oluşturma hakkında bilgi için bkz. [bir uygulamayı yerelleştirin](how-to-localize-an-application.md) . Bir WPF uygulamasını yerelleştirilebilir hale getirmek için geliştiricilerin tüm yerelleştirilebilir kaynakları bir kaynak derlemesinde oluşturması gerekir. Kaynak derlemesi farklı dillere yereldir ve arka plan kodu, yüklemek için kaynak yönetimi API kullanır.

## <a name="example"></a>Örnek

WPF uygulaması için gereken dosyalardan biri bir proje dosyasıdır (. proj). Uygulamanızda kullandığınız tüm kaynaklar proje dosyasına eklenmelidir. Aşağıdaki XAML örneği bunu gösterir.

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

Uygulamanızda bir kaynak kullanmak için, <xref:System.Resources.ResourceManager> kullanmak istediğiniz kaynağı oluşturun ve yükleyin. Aşağıdaki C# kodu bunun nasıl yapılacağını göstermektedir.

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama yerelleştirme](how-to-localize-an-application.md)
