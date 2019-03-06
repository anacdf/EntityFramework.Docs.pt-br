---
title: Salvamento assíncrono – EF Core
author: rowanmiller
ms.date: 01/24/2017
ms.assetid: b64a606e-ecd9-4807-829a-b6ec05ade33f
uid: core/saving/async
ms.openlocfilehash: 6f482a77300ff2930953686751a579b022bf6f77
ms.sourcegitcommit: dadee5905ada9ecdbae28363a682950383ce3e10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42997276"
---
# <a name="asynchronous-saving"></a>Salvamento assíncrono

O salvamento assíncrono evita o bloqueio de uma thread enquanto as alterações são gravadas no banco de dados. Isso pode ser útil para evitar o congelamento da interface do usuário de um aplicativo de cliente espesso. As operações assíncronas também podem aumentar a taxa de transferência em um aplicativo Web, em que a thread pode ser liberada para atender a outras solicitações enquanto a operação do banco de dados é concluída. Para saber mais, veja [Programação assíncrona em C#](https://docs.microsoft.com/dotnet/csharp/async).

> [!WARNING]  
> O EF Core não oferece suporte para várias operações simultâneas sendo executadas na mesma instância de contexto. Aguarde sempre a conclusão de uma operação antes de iniciar a operação seguinte. Isso geralmente é feito usando a palavra-chave `await` em cada operação assíncrona.

O Entity Framework Core fornece `DbContext.SaveChangesAsync()` como uma alternativa assíncrona para `DbContext.SaveChanges()`.

[!code-csharp[Main](../../../samples/core/Saving/Saving/Async/Sample.cs#Sample)]
