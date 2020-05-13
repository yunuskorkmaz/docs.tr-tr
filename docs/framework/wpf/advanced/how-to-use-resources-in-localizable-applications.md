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
# <a name="how-to-use-resources-in-localizable-apps"></a><span data-ttu-id="84620-102">Nasıl yapılır: yerelleştirilebilir uygulamalarda kaynakları kullanma</span><span class="sxs-lookup"><span data-stu-id="84620-102">How to: Use resources in localizable apps</span></span>

<span data-ttu-id="84620-103">Yerelleştirme, bir kullanıcı arabirimini farklı kültürlere uyarlayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="84620-103">Localization means to adapt a user interface to different cultures.</span></span> <span data-ttu-id="84620-104">Bunu yapmak için başlıklar, açıklamalı alt yazılar ve liste kutusu öğeleri gibi metinler çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="84620-104">To do this, text such as titles, captions, and list box items must be translated.</span></span> <span data-ttu-id="84620-105">Çeviriyi daha kolay hale getirmek için çevrilecek öğeler kaynak dosyalarına toplanır.</span><span class="sxs-lookup"><span data-stu-id="84620-105">To make translation easier, the items to be translated are collected into resource files.</span></span> <span data-ttu-id="84620-106">Yerelleştirme için bir kaynak dosyası oluşturma hakkında bilgi için bkz. [bir uygulamayı yerelleştirin](how-to-localize-an-application.md) .</span><span class="sxs-lookup"><span data-stu-id="84620-106">See [Localize an app](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="84620-107">Bir WPF uygulamasını yerelleştirilebilir hale getirmek için geliştiricilerin tüm yerelleştirilebilir kaynakları bir kaynak derlemesinde oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84620-107">To make a WPF application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="84620-108">Kaynak derlemesi farklı dillere yereldir ve arka plan kodu, yüklemek için kaynak yönetimi API kullanır.</span><span class="sxs-lookup"><span data-stu-id="84620-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span>

## <a name="example"></a><span data-ttu-id="84620-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="84620-109">Example</span></span>

<span data-ttu-id="84620-110">WPF uygulaması için gereken dosyalardan biri bir proje dosyasıdır (. proj).</span><span class="sxs-lookup"><span data-stu-id="84620-110">One of the files required for a WPF application is a project file (.proj).</span></span> <span data-ttu-id="84620-111">Uygulamanızda kullandığınız tüm kaynaklar proje dosyasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="84620-111">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="84620-112">Aşağıdaki XAML örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84620-112">The following XAML example shows this.</span></span>

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

<span data-ttu-id="84620-113">Uygulamanızda bir kaynak kullanmak için, <xref:System.Resources.ResourceManager> kullanmak istediğiniz kaynağı oluşturun ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="84620-113">To use a resource in your application, instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="84620-114">Aşağıdaki C# kodu bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84620-114">The following C# code demonstrates how to do this.</span></span>

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a><span data-ttu-id="84620-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84620-115">See also</span></span>

- [<span data-ttu-id="84620-116">Uygulama yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="84620-116">Localize an app</span></span>](how-to-localize-an-application.md)
