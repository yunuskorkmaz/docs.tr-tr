---
title: "Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04dbcfb0fa16ceb4d6778ef611e926894d7840e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="2b8db-102">Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma</span><span class="sxs-lookup"><span data-stu-id="2b8db-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="2b8db-103">Bu örnek bir uygulama kapsamlı özel kaynak sözlüğü tanımlayın ve nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b8db-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b8db-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b8db-104">Example</span></span>  
 <span data-ttu-id="2b8db-105"><xref:System.Windows.Application>Paylaşılan kaynaklar için bir uygulama kapsamı deposu gösterir: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b8db-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="2b8db-106">Varsayılan olarak, <xref:System.Windows.Application.Resources%2A> özelliği olan bir örneğine ilk <xref:System.Windows.ResourceDictionary> türü.</span><span class="sxs-lookup"><span data-stu-id="2b8db-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="2b8db-107">Alma ve ayarlama kullanarak uygulama kapsamı özelliklerini olduğunda bu örneği kullanmak <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b8db-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="2b8db-108">Daha fazla bilgi için bkz: [nasıl yapılır: almak ve bir uygulama kapsamı kaynak ayarlamak](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span><span class="sxs-lookup"><span data-stu-id="2b8db-108">For more information, see [How to: Get and Set an Application-Scope Resource](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span></span>
  
 <span data-ttu-id="2b8db-109">Kullanılarak ayarlanan birden çok kaynaklarınız varsa <xref:System.Windows.Application.Resources%2A>, bunun yerine özel bir kaynak sözlüğü bu kaynakları depolamak ve ayarlamak için kullanabileceğiniz <xref:System.Windows.Application.Resources%2A> onunla yerine.</span><span class="sxs-lookup"><span data-stu-id="2b8db-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="2b8db-110">XAML kullanarak özel bir kaynak sözlüğü bildirme nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b8db-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="2b8db-111">Tüm kaynak sözlüklerindeki kullanarak takas <xref:System.Windows.Application.Resources%2A> uygulama kapsamı temalarını desteklemek, burada her tema kapsüllenmiş tek bir kaynak sözlüğü tarafından sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b8db-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="2b8db-112">Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="2b8db-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="2b8db-113">Aşağıdaki tarafından gösterilen kaynak sözlüğünden uygulama kapsamı kaynaklarını nasıl erişebileceğini gösterir <xref:System.Windows.Application.Resources%2A> XAML'de.</span><span class="sxs-lookup"><span data-stu-id="2b8db-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="2b8db-114">Aşağıdaki nasıl Ayrıca kaynak kodunda alabileceğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b8db-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="2b8db-115">Kullanırken yapmanız gereken iki noktalar vardır <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b8db-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="2b8db-116">İlk olarak, sözlük *anahtar* bir nesne olduğundan özellik değerini alırken ve tam olarak aynı nesne örneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b8db-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="2b8db-117">(Bir dize kullanıldığında anahtarın büyük küçük harfe duyarlı olduğunu unutmayın.) İkincisi, sözlük *değeri* bir özellik değeri alırken değeri istenen türe çevirmeniz gerekir böylece bir nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="2b8db-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8db-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b8db-118">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [<span data-ttu-id="2b8db-119">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="2b8db-119">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="2b8db-120">Birleştirilmiş Kaynak Sözlükleri</span><span class="sxs-lookup"><span data-stu-id="2b8db-120">Merged Resource Dictionaries</span></span>](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
