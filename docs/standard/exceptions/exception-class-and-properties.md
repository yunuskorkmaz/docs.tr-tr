---
title: Özel Durumu Sınıfı ve Özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 283b3b1aa0d56b50b6f9e67b66de3e0b68ae2331
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036352"
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="315fe-102">Özel durum sınıfı ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="315fe-102">Exception class and properties</span></span>

<span data-ttu-id="315fe-103"><xref:System.Exception> Özel durumları devraldığı taban sınıfı.</span><span class="sxs-lookup"><span data-stu-id="315fe-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="315fe-104">Örneğin, <xref:System.InvalidCastException> sınıf hiyerarşisi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="315fe-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="315fe-105"><xref:System.Exception> Sınıfı daha kolay bir özel durum anlama sağlamak, aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="315fe-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="315fe-106">Özellik adı</span><span class="sxs-lookup"><span data-stu-id="315fe-106">Property Name</span></span> | <span data-ttu-id="315fe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="315fe-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="315fe-108">Bir <xref:System.Collections.IDictionary> , anahtar-değer çiftlerinde rastgele verileri tutar.</span><span class="sxs-lookup"><span data-stu-id="315fe-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="315fe-109">Özel durumun nedeni hakkında kapsamlı bilgi sağlayan bir Yardım dosyası, URL (veya URN) barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="315fe-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="315fe-110">Bu özellik, oluşturmak ve özel durum işleme sırasında özel durum bir dizi korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="315fe-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="315fe-111">Daha önce Yakalanan özel durumların içeren yeni bir özel durum oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="315fe-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="315fe-112">Özgün özel durum ikinci özel durum tarafından yakalanabilir <xref:System.Exception.InnerException> özelliği, ek bilgileri incelemek için ikinci özel durumu işleyen kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="315fe-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="315fe-113">Örneğin, hatalı biçimlendirilmiş bir bağımsız değişken alan bir yöntem olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="315fe-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="315fe-114">Kodu bir bağımsız değişken okumaya çalışır, ancak bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="315fe-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="315fe-115">Yöntemi özel durumu yakalar ve oluşturur bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="315fe-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="315fe-116">Bir özel durum nedenini belirlemek için çağıranın yeteneğini artırmak için bazen bir yardımcı yordam tarafından oluşturulan bir özel durum yakalamak ve sonra gerçekleşen hata göstergesi daha özel durum için bir yöntem için uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="315fe-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="315fe-117">Yeni ve daha anlamlı bir özel durum oluşturulabilir, özgün özel durum iç özel duruma başvuru yeri ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="315fe-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="315fe-118">Bu daha anlamlı ardından çağırana özel durum.</span><span class="sxs-lookup"><span data-stu-id="315fe-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="315fe-119">Bu işlevsellik ile önce oluşturulan bir özel durum ile biten bir dizi bağlantılı özel durumları oluşturabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="315fe-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="315fe-120">Özel durumun nedeni hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="315fe-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="315fe-121">Alır veya uygulama ya da hataya neden nesne adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="315fe-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="315fe-122">Bir hata oluştuğu belirlemek için kullanılan bir yığın izlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="315fe-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="315fe-123">Hata ayıklama bilgileri kullanılabiliyorsa, yığın izlemesi kaynak dosya adı ve program satır numarasını içerir.</span><span class="sxs-lookup"><span data-stu-id="315fe-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="315fe-124">Devralınan sınıflar çoğu <xref:System.Exception> değil ek üyelerini uygulama veya ek işlevsellik sağlar; bunlar yalnızca devralınacak <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="315fe-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="315fe-125">Bu nedenle, özel durum sınıfları, özel durum adı ve özel durum'içinde yer alan bilgileri hiyerarşideki bir özel durum için en önemli bilgiler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="315fe-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="315fe-126">Throw ve catch öğesinden türetilen nesneler öneririz <xref:System.Exception>, ancak türetilen herhangi bir nesne oluşturabilecek <xref:System.Object> sınıfı bir özel durum olarak.</span><span class="sxs-lookup"><span data-stu-id="315fe-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="315fe-127">Tüm diller oluşturmak ve yakalamak öğesinden türetilen olmayan nesneler sürümlerin desteklendiğini unutmayın ve <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="315fe-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="315fe-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="315fe-128">See also</span></span>

- [<span data-ttu-id="315fe-129">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="315fe-129">Exceptions</span></span>](index.md)
